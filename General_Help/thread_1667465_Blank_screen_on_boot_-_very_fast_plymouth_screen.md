---
title: "Blank screen on boot - very fast plymouth screen"
date: 2011-01-14
forum: General Help
---

### Post by staf0048 on 2011-01-14
I fixed this issue on 10.04, but just recently (1 hour ago) upgraded to 10.10 and am having the same issue.  Machine boots fine, but the screen is blank for most of the boot, and plymouth is up for about a half second before I get to the login screen.

I've tried searching the threads, but for the life of me I can't find the solution and can't remember what I did to fix it on Lucid.

---

### Post by staf0048 on 2011-01-14
Found my fix:

> create this file.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.

Then

```
sudo update-initramfs -u
```

---

### Post by stinkeye on 2011-01-15
> **staf0048 said:**
> Found my fix:
Thanks for this.
I tried this just to see what it did.
I didn't even realize I was only seeing the last few seconds of plymouth.

**Tip:**Anytime I find any solutions, customization,terminal commands etc
I save them in Gnote.
Has saved me a lot of googling through the various releases.

---

### Post by staf0048 on 2011-01-16
_

---

### Post by staf0048 on 2011-01-16
> **stinkeye said:**
> Thanks for this.
**Tip:**Anytime I find any solutions, customization,terminal commands etc
I save them in Gnote.
Has saved me a lot of googling through the various releases.

Good tip.  I've made several shell scripts to save me from the same headache - not this time for some reason though... :?

---

