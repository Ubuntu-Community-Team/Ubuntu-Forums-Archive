---
title: "Chromium resizing issue"
date: 2009-12-24
forum: General Help
---

### Post by danastasio on 2009-12-24
Hi, I know that this isn't the chromium dev forum, but thats my next stop. Has anyone had any problems with chromium resizing itself? And I mean the whole window, not just the text area. For example, going to the -main google home page- results in a browser that is about 4 monitors long. And by that, I mean if you hold down alt, or whatever your particular hotkey is for grabbing windows, you have to drag your mouse up your screen four times to reach the bottom of the browser. Also, many times while doing this insanity, it will simply refuse to work right. For example, it will "jump" all around my computer. Not just my screen, I have 8 work spaces, (two rows of four) and when clicking inside the browser, it almost bounces around and moves to a different work space. It kinda just picks one at random. Or it will maximize the window when clicking in the middle of the screen... I have it installed from the google PPA. I've no idea how to troubleshoot this.

```
dave@dave-laptop:~$ chromium-browser
/home/dave/.themes/Christmas time/gtk-2.0/menubar.rc:79: error: unexpected character `{', expected keyword - e.g. `style'
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:216: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:219: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:223: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:226: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:230: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:233: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:237: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:240: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:339: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:342: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:347: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:350: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:355: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:358: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:363: Unable to locate image file in pixmap_path: "none.png"
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:366: Background image options specified without filename
/home/dave/.themes/Christmas time/gtk-2.0/gtkrc:743: error: invalid string constant "list-header", expected valid string constant
Created new window in existing browser session.
dave@dave-laptop:~$ 

```

---

### Post by FreezWay on 2009-12-24
im having the same issue

EDIT: mine gets smaller not larger

---

### Post by fragos on 2009-12-25
Me too, particular sites expand the window to th entire page even if that's bigger than your screen. I've filed a bug with Chromium bug 31084. You can add on here [http://code.google.com/p/chromium/issues/detail?id=31084&q=google%20analytics&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS](http://code.google.com/p/chromium/issues/detail?id=31084&q=google%20analytics&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS)

---

### Post by A_T on 2009-12-25
I'm having this problem too.

---

### Post by jbcfarina on 2009-12-25
me too

Edit:I think it is this bug

[http://code.google.com/p/chromium/issues/detail?id=30995](http://code.google.com/p/chromium/issues/detail?id=30995)

...:-(

---

### Post by fragos on 2009-12-25
> **jbcfarina said:**
> me too

Edit:I think it is this bug

[http://code.google.com/p/chromium/issues/detail?id=30995](http://code.google.com/p/chromium/issues/detail?id=30995)

...:-(

I think you're correct. The bug I found was a special case of the same bug.

---

### Post by SnappyU on 2009-12-26
I started experiencing this same bug for a few days now.

Chromium 4.0.281.0 (35262) Ubuntu Jaunty

Repo steps:
1. Open some flash video page
2. Scroll up and down.
3. Click on blank space on the web page.
4. Whole Chromium app/window resizes.

In my case, the resizing happens in sync with the mouse wheel scroll.

I spent some time troubleshooting, thinking it is some compiz effects bug or the new Adobe flash 10 that is buggy.  Turns out it only happens in Chromium.

For me, it only happens with flash video.

EDIT:

From google chromium site:
> Comment 32 by [email]evan@chromium.org[/email], Yesterday (17 hours ago)
Thanks for the details everyone, but the bug is in the "started" state which means 
we're working on a fix, and it will be updated when it's fixed.  No more comments are 
necessary.

> Comment 37 by [email]evan@chromium.org[/email], Today (113 minutes ago)
Taking myself off cc since y'all are incapable of reading comment #32.  :)

---

### Post by fragos on 2009-12-26
> **SnappyU said:**
> I started experiencing this same bug for a few days now.

Chromium 4.0.281.0 (35262) Ubuntu Jaunty

Repo steps:
1. Open some flash video page
2. Scroll up and down.
3. Click on blank space on the web page.
4. Whole Chromium app/window resizes.

In my case, the resizing happens in sync with the mouse wheel scroll.

I spent some time troubleshooting, thinking it is some compiz effects bug or the new Adobe flash 10 that is buggy.  Turns out it only happens in Chromium.

For me, it only happens with flash video.

EDIT:

From google chromium site:

Thanks for the update. I had no doubt a bug so pervasive wouldn't be fixed and indeed a fix is in the works. They got the message, let's stop the commenting in the bug reporting system so they can get to work.

---

### Post by jbcfarina on 2009-12-26
Seems to work with the las update,...

---

### Post by fragos on 2009-12-26
4.0.283.0 (Developer Build 35283) Ubuntu is just out. I tested with web pages that caused this problem and couldn't reproduce. The Chromium team is 1st class and deserving of our appreciation.

---

### Post by pt123 on 2009-12-26
same here
happened on IMDB 

Good to see it wasn't just me

Makes chromium unusable

---

### Post by cmwslw on 2009-12-27
I'm on the latest Launchpad PPA for Chromium and get this bug. It only happens when I have flash installed and visit a flash page. So from what I understand it is fixed in the latest source? If so, tomorrows PPA might fix it.

---

### Post by danastasio on 2009-12-28
AWESOME!!! Just installed the update and it works :D
Thanks!

---

