---
title: "Conky RSS troubles"
date: 2012-05-14
forum: General Help
---

### Post by Nintendo01 on 2012-05-14
I am having some issues getting conky's RSS feed feature to work. Here is part of my conkyrc:

```

${rss www.nhc.noaa.gov/index-at.xml 15 item_title 0}
${rss www.nhc.noaa.gov/index-at.xml 15 item_desc 0}
-----
${rss www.nhc.noaa.gov/index-at.xml 15 item_title 1}
${rss www.nhc.noaa.gov/index-at.xml 15 item_desc 1}

```

And this goes to item number 4. It will pull the title properly every time, but if the item_desc has any html in it it seems to break. Currently, the item 0 information has simple text for the item_desc and it is showing properly, but the item 1 item_desc has html in it and begins with ![CDATA[. Running conky via the terminal shows that it's not throwing any errors, it's just not displaying anything.

I've googled this in many different ways and can't find any information on making this work. Everyone else seems to only want the titles on their conky RSS feeds and doesn't bother with the item_desc. Can anyone shed some light on this?

---

