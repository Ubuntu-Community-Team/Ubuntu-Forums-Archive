---
title: "Firefox shows some pages as binary(?)"
date: 2012-02-01
forum: General Help
---

### Post by Cybolic on 2012-02-01
On some pages - I haven't been able to find a pattern in which - Firefox show nothing but what appears to be binary code rendered as text.

Example:
[ATTACH]211788[/ATTACH]

I'm using the version from the mozillateam/firefox-next PPA.

Has anyone experienced this or know a fix?

---

### Post by Cybolic on 2012-02-01
Also, saving the page from either the main window or from the view source window, saves the .html file correctly... it's very weird.

---

### Post by sanderd17 on 2012-02-01
Strange, can you try with a fresh profile?

You can rename your .mozilla directore (it's hidden, show it with CTRL+H in nautilus) to something else, so firefox doesn't find it any more and will create a new profile.


```

mv .mozilla mozilla-backup

```

---

### Post by Cybolic on 2012-02-01
Strange, that worked!
Thanks for the tip :D

---

### Post by sanderd17 on 2012-02-02
> **Cybolic said:**
> Strange, that worked!
Thanks for the tip :D

It has to be some setting, somewhere.

You have now lost all your bookmarks and history etc (unless you set up sync I believe). But they aren't totally lost. You can get them back by switching the directory names again. But that will cause the pages to render in binary too.

So it's only good to get some info, temporarily.

---

### Post by Cybolic on 2012-02-02
Yeah, don't worry, I know how it functions ;)
I just had that close bond to my tabs before, and didn't really want to see them go - luxury problem, I know.

If only I could grep the sqlite database to see where the settings differ, but never mind - I didn't have much that wasn't already in Chrome.

---

