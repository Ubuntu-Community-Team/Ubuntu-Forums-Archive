---
title: "Digg RSS feeds in Conky"
date: 2011-09-15
forum: General Help
---

### Post by undfined on 2011-09-15
I got Slashdot working and some other RSS feeds.  Digg just won't work.  No errors but no data is showing up.

Here's the relevant section:

```
#RSS
${font Arial:style=Bold:size=10}${rss http://rss.slashdot.org/Slashdot/slashdot 10 feed_title} ${font} ${hr 2}
${rss http://rss.slashdot.org/Slashdot/slashdot 60 item_titles 5}
${font Arial:style=Bold:size=10}Digg ${font} ${hr 2}
${rss http://services.digg.com/2.0/story.getTopNews?type=rss 60 item_titles 5}
```

I think I just stared at this too long and am missing syntax or something.

Thanks ahead.

---

