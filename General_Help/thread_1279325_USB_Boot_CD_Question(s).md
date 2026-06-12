---
title: "USB Boot CD Question(s)"
date: 2009-09-30
forum: General Help
---

### Post by tim22b on 2009-09-30
To make a long story short:

My laptop that was running Ubuntu 9.04 died.  I managed to salvage the hard drive and put it in an enclosure that makes it act like a USB hard drive so I could use it in another desktop computer I had lying around.  Worked fine.  When I went to go make a different computer boot from it, I ran into a problem.

The computer is perfectly happy booting from a USB or internal CD drive, so I figured I'd try to make a USB boot cd.  I made a Super GRUB Disc, which works fine itself.

I suppose my first question is was that the right thing to do/should it even work for what I want it to do.  Also, apparently the disc uses grub 2.0, and the hard drive still has grub 1.5 on it, will that cause a problem?

When I attempt to boot my hard drive, I can find it and everything works ok until I attempt to do the "chainloader +1" command from the grub command line.  It replies with, "Error 13: Invalid or unsupported executable format."

So my next question is: is this problem related to the fact that, as I understand it, I'm trying to boot grub with grub?  If it is, is there any kind of workaround, and if it isn't, what am I doing wrong?

When I get to the grub command line, I type:

```

rootnoverify (hd0,0)
makeactive
chainloader +1

```
It's hd0 because my computer doesn't have an internal hard drive.

Thanks!

---

