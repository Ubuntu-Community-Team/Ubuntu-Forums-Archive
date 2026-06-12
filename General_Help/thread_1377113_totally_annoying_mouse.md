---
title: "totally annoying mouse"
date: 2010-01-09
forum: General Help
---

### Post by HellionDarkLord on 2010-01-09
There seems to be an issue with my mouse.  This issue is present whether working in Ubuntu 9.10, or Windows 7.  The mouse stops responding for a moment or two every little bit.

At first I thought the problem came from power management, but that doesn't seem to be it.

I tried disabling hpet, and a host of other things.  Nothing works at all, and yes, I tried using another mouse.

my system is nice and new 

K9N6PGM2-v main
N260GTX OCv4 graphics
Phenom x3 proc
logitech nX80 mouse

---

### Post by kman269 on 2010-01-09
The fact that it has the same problem on windows and ubuntu makes it sound like a hard ware problem. I would try a different mouse or try that mouse in a different computer.

---

### Post by HellionDarkLord on 2010-01-10
Okay, I read somewhere that the cool'n quiet AMD stuff can cause mice to do this.  However, I can't find a way to disable it in bios which sucks for windows, but I am removing acpid and other power saving stuff from Ubuntu to see if that will help. So far, it is working.

I've been using ```
update-rc.d
``` to disable all the laptop and power saving things, but for some reason acpid still starts and runs.

Anybody know why that is?

I have to say that my system is much faster now that I have removed things like ppp-dns that I really don't need. (I mean TONS faster boot time!)

Honestly, I didn't know how much faster my system would be by doing this.:shock:

---

### Post by HellionDarkLord on 2010-01-10
I've tried other mice, serial, and usb.  No difference.

---

### Post by HellionDarkLord on 2010-01-13
FINALLY!!!

So I decided I didn't want all the magical effects that compiz provides.

Whalla!! no more mouse issues.  I have completely uninstalled compiz and now my mouse works wonderfully!  YAY!!!

---

