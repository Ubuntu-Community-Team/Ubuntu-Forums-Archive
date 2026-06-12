---
title: "xmms crashes"
date: 2006-04-29
forum: General Help
---

### Post by Finster101 on 2006-04-29
Hi,

When I am using xmms to play my mp3s or to play a CD it will suddenly just quit and disappear off the desktop (crash).  It even happens when I scroll through my list of mp3s with the scrollbar or my middle mouse button.

I ran it from a terminal to see if I could capture any error messages and I got something like this:
Segmentation fault

You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.

Xlib: unexpected async reply (sequence 0x319a)!

So is this a problem with Xlib or xmms?  Any easy way to fix this problem besides switching to a different player?  I'm using 5.10 and xmms 1.2.10 (the one that comes with ubuntu) and alsa sound.

Thanks

---

### Post by bluevoodoo1 on 2006-04-29
I found this for you...
[http://bugs.xmms.org/show_bug.cgi?id=405](http://bugs.xmms.org/show_bug.cgi?id=405)

---

### Post by [pl]ice on 2006-04-29
hey,
 try wiping all ur settings ~/.xmms rename it, this often helped me ... with things like that, other thing is that u have some plugin running that crashed the thing; eg. wma plugin(crashes my xmms) or iTouch, play with it,
good luck ;)

---

