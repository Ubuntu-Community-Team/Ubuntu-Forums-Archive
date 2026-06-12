---
title: "TTYs not working"
date: 2011-01-08
forum: General Help
---

### Post by J V on 2011-01-08
None of my ttys work (Except X)

When I switch to a tty to fix a problem that's locked up Xorg, after a few seconds of black my screen says "No DVI signal"

This is not a problem with my screen as I can go right back to tty7 and get my (Albeit locked up) X back...

Anyone know why my system is doing this?

---

### Post by tredegar on 2011-01-08
What graphics card do you have?
If NVIDIA, are you using their driver?

---

### Post by efflandt on 2011-01-08
If running 10.04, did you try **nomodeset** kernel boot parameter?  For example I had to do that with old legacy ATI X1300 (desktop or laptop) using default video drivers in 10.04, although, that seems to be fixed in 10.10.  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

---

### Post by J V on 2011-01-08
I'm using the latest nvidia driver on a 9500 GT. I'll try out nomodset and see what that gets me.

---

### Post by tredegar on 2011-01-08
By all means try nomodeset.

But I guessed correctly that you have an NVIDIA driver.
[This post]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") is about "Fixing the ugly plymouth bootsplash" but the real gem is that it fixes up the (broken) framebuffer.

Just follow the instructions for "Alternative One". I am not interested in the bootsplash, but it fixed the virtual terminals on tty-F1 - tty-F6

---

