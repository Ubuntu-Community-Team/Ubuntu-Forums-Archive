---
title: "Huge cursor with xserver-xgl"
date: 2010-08-13
forum: General Help
---

### Post by naurus on 2010-08-13
Hello,
I got quad monitors running with compiz effects by using the old xserver-xgl package.  The only problem is that my cursors are HUGE!

[IMG]http://img707.imageshack.us/img707/1172/imgpwg.jpg[/IMG]

During the login screen the cursor is fine but after I log in it gets like that.  If I go into either KDE settings or Gnome settings and change the cursor theme a couple times it will go back to normal for a while but eventually change back to the huge size.  I've tried both SWCursor and HWCursor in xorg.conf and SWCursor just created more problems as usual.

I'm running 4 separate X screens with xinerama to connect them all.  I think the kicker here is the xserver-xgl package.

Another clue, when I was editing my xorg.conf to get all the monitors working if I had just the bottom two screens or top two screens working I would have a normal mouse.  I believe the big mouse happened when I had the top-left and bottom-right screens working as well as with all 4 working, so I'm pretty sure it has something to do with how many rows of monitors I have (the cursor is exactly 2x bigger than normal which corresponds perfectly with having 2 rows of monitors as opposed to the normal 1 row)

Thanks in advance,
Naurus

---

