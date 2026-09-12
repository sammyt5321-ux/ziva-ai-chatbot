# ✨ Ziva AI - Smart AI Chatbot

A beautiful, modern AI chatbot interface with a gradient UI built with vanilla HTML, CSS, and JavaScript.

## Features

- 🎨 **Beautiful Gradient UI** - Modern dark theme with vibrant pink/purple gradients
- 💬 **Real-time Chat** - Smooth message sending and receiving
- 🤖 **AI Powered** - Connects to your AI backend via Cloudflare Workers
- 📱 **Responsive Design** - Works on desktop, tablet, and mobile
- ⚡ **Lightweight** - No dependencies, pure vanilla JavaScript

## Setup Instructions

### Step 1: Deploy to GitHub Pages

This app is ready to deploy instantly! GitHub Pages will automatically serve your `index.html`.

1. Go to your repository settings
2. Navigate to **Pages** section
3. Select **Deploy from a branch** (if not already selected)
4. Choose **main** branch and root folder
5. Click **Save**

Your chatbot will be live at: `https://sammyt5321-ux.github.io/ziva-ai-chatbot`

### Step 2: Connect Your AI Backend

To enable the chatbot to respond, you need to connect a Cloudflare Worker:

1. Create a Cloudflare Worker at [workers.cloudflare.com](https://workers.cloudflare.com)
2. Add your AI API logic (OpenAI, Cohere, Hugging Face, etc.)
3. Copy your Worker URL
4. Edit `index.html` and replace `PASTE_YOUR_WORKER_URL_HERE` with your Worker URL
5. Commit and push the changes

### Example Cloudflare Worker (OpenAI)

```javascript
export default {
  async fetch(request) {
    if (request.method === 'POST') {
      const { message } = await request.json();

      const response = await fetch('https://api.openai.com/v1/chat/completions', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer YOUR_OPENAI_KEY`
        },
        body: JSON.stringify({
          model: 'gpt-3.5-turbo',
          messages: [{ role: 'user', content: message }]
        })
      });

      const data = await response.json();
      const reply = data.choices[0].message.content;

      return new Response(JSON.stringify({ reply }), {
        headers: { 'Content-Type': 'application/json' }
      });
    }
  }
};
```

## Live Demo

Once GitHub Pages is enabled, visit:
🔗 **https://sammyt5321-ux.github.io/ziva-ai-chatbot**

## Project Structure

```
ziva-ai-chatbot/
├── index.html          # Main chatbot interface
└── README.md          # This file
```

## Technologies

- HTML5
- CSS3 (Gradients, Flexbox)
- Vanilla JavaScript (ES6+)
- Cloudflare Workers (backend)

## Customization

### Change Colors
Edit the CSS gradient colors in `index.html`:
```css
background:linear-gradient(135deg,#ff1493,#9b2cff,#5b21b6);
```

### Change Title & Description
Update the header text:
```html
<h1>✨ Ziva AI</h1>
<p>Your smart AI assistant</p>
```

## Support

Need help? Check the comments in `index.html` for setup instructions and troubleshooting tips.

---

**Made with ❤️ by Ziva AI**