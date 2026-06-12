---
title: "Desktop RSS Reader?"
date: 2011-06-18
forum: General Help
---

### Post by Robert Finley on 2011-06-18
Can anyone suggest a RSS reader?  I'm trying to find a transparent reader that will sit in the background on my desktop.

I tried Yarssr.  Not exactly what I wanted. The gdesklet RSS reader is just what I want but I'd like to find something a little lighter weight.  I am working on figuring out how to just make conky do it, but I'm not quite there yet.

Any recommendations?  Is conky the way to go?

---

### Post by Habitual on 2011-06-19
> **Robert Finley said:**
> Is conky the way to go?

Yep.

---

### Post by Robert Finley on 2011-06-20
Aww yeah! The more I play with conky, the more I love it.  I've got my RSS feed running on my desktop now.  I am working with a stock ubuntu conky script and just modifying to suit my needs.  This is what I used to get the feed:

${color 1793d1}NPR News:${color ffffff}
${rss [http://www.npr.org/rss/rss.php?id=1001](http://www.npr.org/rss/rss.php?id=1001) 10 item_titles 30 }

Can someone please tell me in plain english what the 10 and the 30 at the end represent?

---

### Post by Toz on 2011-06-20
The 10 represents the time refresh interval and the 30 represents the number of most recent "item_titles" (the items or topics in this feed) to display.

---

### Post by Robert Finley on 2011-06-20
> **Toz said:**
> The 10 represents the time refresh interval...

in seconds?

---

### Post by Toz on 2011-06-20
No, in minutes.

---

### Post by Robert Finley on 2011-06-20
Thank you for your help.  Ubuntu's support community is what makes it truly great.

---

