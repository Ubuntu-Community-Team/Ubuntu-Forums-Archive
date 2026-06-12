---
title: "trouble booting natty from usb.."
date: 2010-11-12
forum: General Help
---

### Post by owners4life5 on 2010-11-12
hello,

i installed today.s (11-12-10) daily build of natty off of the site, and installed it to a usb, making a live cd out of it.

anyway, when it is booting, i select 'try ubuntu without installing', blah-blah-blah...then it just hangs on the gui...only showing the mouse, and the wallpaper that is identical to the maverick default.

so i go to the cli by ctrl+alt+f2, and try to update to see if maybe that can fix the problem.

so this is what happens:
```
brian@brian-gateway:~$ sudo apt-get update
apt-get: error while loading shared libraries: libz.so.1: cannot close file descriptor: Input/output error
```

and now i.m at a standstill...i bought a new 8gb usb drive this afternoon to try this out, looking forward to it and everything...i mean, i wasn.t expecting much, it isn.t even in alpha yet.

but i.m at a standstill, and am open to suggestions.

so if anyone would like to throw one at me, feel free to.

thanks in advance,

---

### Post by dcstar on 2010-11-12
> **owners4life5 said:**
> hello,

i installed today.s (11-12-10) daily build of natty off of the site, and installed it to a usb, making a live cd out of it.
........

**All** issues with development versions belong in the relevant development forum.

---

### Post by owners4life5 on 2010-11-12
excuse my ignorance...please move this thread if necessary.

---

### Post by owners4life5 on 2010-11-14
bump

---

### Post by owners4life5 on 2010-11-15
anyone?

---

### Post by owners4life5 on 2010-11-16
bump

---

### Post by KBD47 on 2011-08-20
I will add this here even though it is an old post. None of the following Ubuntu's worked well from a live persistent usb, not 10.04, 10.10, or 11.04 every one of them would hang at the 'try' or 'install' window. I finally realized that I could close that window, force shutdown, and then wait about 5-7 minutes and they would eventually let me finish booting. Now I also tried 11.04 from non-persistent live usb created by Unetbootin and it also had problems, namely after it booted it would not launch Firefox when you clicked on that app. I reformatted and tried this twice with the same results.
  I point this out because it nearly caused me to pass on Ubuntu altogether, indeed I did for awhile. Because I could get Linux Mint 9 and 11 to run flawlessly from both a live usb and a live persistent usb which made me feel those were more stable. I'm sure I'm not the only one who likes to test drive an OS before installing it. Having now installed Ubuntu on my computer it works flawlessly, but the above problems may put off those who want to try it from live usb first, and would otherwise want to install Ubuntu. Worth considering.
KBD47

---

