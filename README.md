
<h1 align="center">Hanime.tv Scraper</h1>

<p align="center">
  A powerful scraper built to fetch trending videos from <a href="https://hanime.tv">Hanime.tv</a>, crafted with care by the <strong>ShizoXteam</strong>.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square" />
  <img src="https://img.shields.io/badge/Made%20by-ShizoXteam-blueviolet?style=flat-square" />
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-square" />
</p>

---

## Features

- **Trending Videos Fetching**
  - Instantly scrape a list of currently trending videos on Hanime.tv
  - Get detailed metadata like:
    - Title
    - Views
    - Thumbnail
    - Tags

---

## Upcoming Features

- **Video Downloader**
  - Download videos directly from Hanime.tv (Coming Soon)

---

## Usage Example

```js
import { hanimeApi } from './hanime.js';

let handler = async (m, { conn }) => {
  try {
    const time = 'week';  // Example: 'day', 'week', or 'month'
    const page = 1;
    
   const trendingVideos = await hanimeApi.getTrending(time, page);
    if (trendingVideos.length === 0) {
      return conn.reply(m.chat, 'No trending videos found at the moment.', m);
    }
    let replyMessage = 'Trending Videos:\n\n';
    trendingVideos.forEach((video, index) => {
      replyMessage += `${index + 1}. ${video.name}\nLink: ${video.link}\nViews: ${video.views}\n\n`;
    });
    return conn.reply(m.chat, replyMessage, m);
  } catch (error) {
    console.error('Error fetching trending videos:', error);
    return conn.reply(m.chat, 'Sorry, there was an issue fetching trending videos. Please try again later.', m);
  }
}

handler.help = ['trending'];
handler.tags = ['nsfw'];
handler.command = /^(trending)$/i;

export default handler;
```

**Example Output:**

```json
[
  {
    "title": "Succubus Service - Episode 1",
    "views": "120K",
    "thumbnail": "https://static-assets.hanime.tv/thumbnail123.jpg",
    "tags": ["Fantasy", "Big Breasts", "Demon Girl"]
  }
]
```

---

## About

This project was developed with passion by the **ShizoXteam**  
We build bots, automation tools, and APIs with performance and scalability in mind.

For collaboration, support, or inquiries, reach out to us on [GitHub](https://github.com/shizoxteam) or your preferred platform.

---

## Disclaimer

> This tool is meant for **educational and personal use only**.  
> We are **not affiliated** with Hanime.tv.  
> Please respect content creators and the site's [Terms of Service](https://hanime.tv/terms).

---

## License

This project is licensed under the [MIT License](LICENSE).
