---
title: "Trimming RSS Feed Titles"
date: 2010-04-06
forum: General Help
---

### Post by Jaded Misanthrope on 2010-04-06
I'm trying to set up Conky to show a number of RSS feeds, and while I can get it to show the raw titles of items how would I trim these titles down to a given number of characters (say, 40) and add an ellipsis to the end if text has been cut off? The length of titles by default can vary wildly, so if only for the sake of organisation it'd be nice to have a maximum title length imposed.

I found [this]("http://ubuntuforums.org/showthread.php?t=1172278") thread that does something kind of similar for Transmission torrents, but I have no idea how I'd adapt it for RSS feeds. As it stands, the code (well, a sample at least) is simply:
```
SLASHDOT$hr
${rss http://rss.slashdot.org/Slashdot/slashdot/to 5 item_title 0}
${rss http://rss.slashdot.org/Slashdot/slashdot/to 5 item_title 1}
${rss http://rss.slashdot.org/Slashdot/slashdot/to 5 item_title 2}
${rss http://rss.slashdot.org/Slashdot/slashdot/to 5 item_title 3}
${rss http://rss.slashdot.org/Slashdot/slashdot/to 5 item_title 4}
```

---

### Post by Jaded Misanthrope on 2010-04-14
Does anybody have any suggestions?

---

