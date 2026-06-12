---
title: "Copying Links To Desktop"
date: 2010-09-19
forum: General Help
---

### Post by jereece on 2010-09-19
When in Chrome or Firefox periodically I want to place a shortcut to a web page on my desktop.  To do this I click on the button just to the left of the address and drag it up to the desktop.  Sometimes this works but more often this creates a copy of the HTML page. And if the web page is HTTPS I get an error.  I can drag to the Bookmarks Bar and it copies the link fine.  Then I can drag it from the Bookmarks Bar to the desktop.  I know I can create a launcher for the web page on my desktop but that's a lot of trouble.  Why would dragging to the desktop work sometimes and not others?  Are there any work arounds or fixes?  I am using Ubuntu 10.4, Chrome 6.0.472.53 and FF 3.6.10.

Thanks,
Jim

---

### Post by afrowildo on 2010-09-20
I think this is what you're looking for, and it appears you may be out of luck.
[http://www.google.co.uk/support/forum/p/Chrome/thread?tid=4c3a7bd13c630eaa&hl=en&fid=4c3a7bd13c630eaa00047216043f1120&hltp=2](http://www.google.co.uk/support/forum/p/Chrome/thread?tid=4c3a7bd13c630eaa&hl=en&fid=4c3a7bd13c630eaa00047216043f1120&hltp=2)

---

### Post by jereece on 2010-09-20
I'm confused.  You say I may be out of luck but the link you sent to me seems to say I should be able to do what I am trying to do.  However in Ubuntu it works sometimes but more often it does not work.  The forum post you sent me to was specific to Google Chrome.  My problem, I think, has to do with Ubuntu.  Dragging the address to the desktop in Windows under Chrome or Firefox or IE has always worked.  However in Ubuntu it only works once in a while.  Sometimes I won't work, then when I try it a second time it works.  
So the problem seems to be with Ubuntu.

Any one else have this experience?  Is this a bug with Ubuntu?

Thanks,
Jim

---

### Post by Dustin2128 on 2010-09-20
hm, you might consider just writing the link by hand, it's not hard. Just write something like this in gedit and save it as a .sh
```
#/bin/bash
firefox [www.nameofwebsite.com]("http://www.nameofwebsite.com")
```you can replace firefox with the browser of your choice, e.g. chromium-browser. Anyway, saving at a .sh saves it as a shell script. When you click on it, it executes the script as a terminal command that tells firefox to open to that particular page.

---

### Post by zitch on 2010-09-20
I'm not seeing this issue at all on Ubuntu 10.04 (64-bit) running Firefox 3.6.10, even with several https sites.  It seems to successfully create the desktop every time on every website I've tried, dragging from the button (usually showing the site's favicon) to the left of the address bar to my desktop.  It creates a file in my ~/Desktop directory with the following data if I do this from the main ubuntu forums:

Name: "Ubuntu Forums.desktop"
Contents: ```
[Desktop Entry]
Encoding=UTF-8
Name=Link to Ubuntu Forums
Type=Link
URL=http://ubuntuforums.org/
Icon=gnome-fs-bookmark

```

It could be something different about the sites you're trying this on or something different with your install. Are you noticing any patterns on what sites this fails on?  Or did you install Firefox from outside the main Ubuntu repos? Possibly any add-ons interfering with this?

Now this is trying it with Firefox; Chromium seems to work differently, in that when I try to do the same, it seems to be trying to make a copy of the site on the desktop and fails.  Now, if I go into Tools->Create Application Shortcuts... in the menu system, it will create a "desktop app" version (no tabs, address bar, browser menu, or the standard browser buttons) of the site on the desktop and menu system, but I would think that's not exactly what you were looking for.  This was Chromium 6.0.472.53, installed from the Ubuntu Software Center if I remember correctly.

---

### Post by jereece on 2010-09-20
I tried this with FF on the ubuntuforums.org main web site and it worked, however I tried it on an HTTPS web site and it did not work.  It seems to work sporadically with FF and Chrome.  Maybe I need to uninstall and reinstall FF and Chrome?

---

### Post by afrowildo on 2010-09-21
Sorry for the confusion. I read neither your question nor the thread I linked to properly.

I really shouldn't post here when tired :)

---

### Post by lovinglinux on 2010-09-21
Try [deskCut]("https://addons.mozilla.org/en-US/firefox/addon/66/")

---

