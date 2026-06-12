---
title: "Disable laptop monitor?"
date: 2012-04-07
forum: General Help
---

### Post by elsieboy on 2012-04-07
Hey all,

I have a laptop with a broken screen that I'm going to use as a samba server. I've installed ubuntu server and can successfully ssh in and do a remote X session. All good.

But I don't want the laptop screen coming on (it's cracked) - it generates heat and wastes power. How do I go about disabling it?

It's an acer aspire one netbook.

Thanks!

---

### Post by ATAQ on 2012-04-07
I have the same Laptop, press the function key and F6 to turn off the screen. Its the handiest way.

---

### Post by papibe on 2012-04-07
It may be possible to turn it on with lid closed if it supports WOL.

Just a thought.
Regards.

---

### Post by schulwitz on 2012-05-31
Looking for the same thing, I found this forum:
[https://bbs.archlinux.org/viewtopic.php?id=66169](https://bbs.archlinux.org/viewtopic.php?id=66169)

Just enter this into a terminal to turn off:
```
vbetool dpms off
```and this to turn it back on:
```
 vbetool dpms on 
```

---

