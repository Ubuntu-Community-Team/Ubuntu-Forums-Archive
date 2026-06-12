---
title: "(K)Ubuntu 9.10 64bit + Radeon HD3200 + font size at virtual console"
date: 2010-02-14
forum: General Help
---

### Post by SushiR on 2010-02-14
I've read so many howto's and threads but never managed to get a decent font size on my tty's. Before grub2 I used to use vga=795 (or something like that), but now that isn't working anymore.

I have a 24" Samsung screen and the font size is HUGE. Has anyone with **same hardware** succeeded in setting a decent resolution? I've played around with gfxpayload and all that stuff, but that doesn't help. I'm using fglrx driver on an up-to-date system.

Any help is appreciated!

---

### Post by flippo on 2010-02-14
I don't have the same hardware, but I have recently configured my tty's to have a MUCH better resolution (1440x900).  

I use the vesafb (its a generic framebuffer) and you have to load it as a kernel prameter.  I use grub-legacy, so my kernel line in menu.lst looks like:

```
kernel <kernel loc> root=<device> edd=off video=vesafb:mtrr:3,ywrap vga=<vganum> <other options>
```

I don't remember why the edd=off is there, or if it is essential.  To get the vganum variable you can type:
```
sudo hwinfo --framebuffer
```

NOTE: if your not using grub-legacy your kernel line wont be in menu.lst and may be different (I've never used grub2).

---

### Post by SushiR on 2010-02-14
Hello flippo,

thanks for your answer, but...

I am looking for a solution for grub2 (as I wrote). Things work differently there.

So if anybody out there has managed to get a decent resolution with a Radeon HD3200 on Ubuntu 9.10...

---

### Post by flippo on 2010-02-14
My soulution should work for grub2, once you boot the kernel its all the same, just look up how to pass the kernel arguments I gave you into grub2.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

