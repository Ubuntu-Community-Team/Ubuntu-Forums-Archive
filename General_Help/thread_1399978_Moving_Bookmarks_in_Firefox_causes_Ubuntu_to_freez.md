---
title: "Moving Bookmarks in Firefox causes Ubuntu to freeze"
date: 2010-02-06
forum: General Help
---

### Post by jereece on 2010-02-06
I posted this yesterday but it appears it got deleted somehow, so here it is again.

I am fairly new at Linux.  I am running Ubuntu 9.10 on my desktop computer which runs a Core 2 Duo at 3.2ghz and I have 2 gig of RAM.  I have installed all the latest Ubuntu updates.

In Firefox, I have about 70 bookmarks in the bookmarks toolbar.  Obviously the bar can't show 70 so most of them are in the dropdown section of the bar on the right.  When I add a new bookmark, Firefox adds it to the end of the dropdown.  Sometimes I want them to be closer to the top so I scroll down, click and drag it up closer to the top.  In Firefox under Windows this works fine.  However in Firefox under Ubuntu, as soon as I start to drag it up Firefox turns gray and Ubuntu totally locks up. Everything in Ubuntu freezes. The main bar at the top stays color, only Firefox turns gray.  I tried clicking around but it's frozen.  I tried pressing Esc, ctrl-alt-delete, and a number of other keys but noting will unfreeze Ubuntu.  I have to physically turn off my computer and reboot.

I have tried this several times and it happens each time.

Any suggestions on what is causing this, how to fix it or how to get my new bookmark near the top?

As always I appreciate the help,

Jim

---

### Post by lovinglinux on 2010-02-06
It would be advisable to vacuum your profile databases. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). The direct link to the Database Optimization instructions is [this one](http://lovinglinux.megabyet.net/?page_id=220#Database--Optimization-1) (my blog). This should fix most bookmark performance issues.

If that doesn't help, then it could be an extension causing the problem. This happened to me once and it was caused by Open Book.

In this case, close Firefox then start it from a terminal using the following command:

```
firefox -safe-mode
```

This will make Firefox start with extensions disabled. Then try to move your bookmarks. If it works, then you need to find which extension is causing this, by disabling them all and enabling one by one, then trying to move the bookmarks. It should be an extension related to bookmarks.

Anyway, you could also try to export your bookmarks using the bookmark organizer, then close Firefox, then delete the file *places.sqlite* from your Firefox profile, which is located under ~/.mozilla/firefox/<profilename>, then start Firefox again so it can create a new *places.sqlite* file and then import the bookmarks back from your backup.

---

