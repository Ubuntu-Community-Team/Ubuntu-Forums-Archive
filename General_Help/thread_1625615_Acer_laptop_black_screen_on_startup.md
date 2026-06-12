---
title: "Acer laptop black screen on startup"
date: 2010-11-19
forum: General Help
---

### Post by bizpeecocck on 2010-11-19
I'm having problems with the screen going black on startup in 10.10. It appears to go completely off (no backlight or anything). If I press ctri+alt+f1 I get a terminal, then I can ctrl+alt+f7 and the desktop appears.
I have tried setting the mode to the correct resolution in xorg.conf and I tried using the vesa driver, but it still doesn't work.

My graphics card shows as sis 661/741/760

Any help will be greatly appreciated.

---

### Post by cavalier911 on 2010-11-19
Based on your description it sounds like your system can't deal with vga16 frame buffer required for the pretty splash. This is how I blacklist it on all my installs to speedup boot time and get verbose startup messages.



Open terminal:

```
sudo bash
```

Enter your password to become root

```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```

Updating the initramfs takes close to 10 minutes on my celeron 400.

**Be Patient!**

```
update-initramfs -u
```

You may want to stop splash from starting which is pretty ugly without the framebuffer so you can see verbose messages.

---

### Post by bizpeecocck on 2010-11-21
Thanks for your reply. I followed your instructions but unfortunately there was no change.

Updating  initramfs only seemed to take about 20 seconds, perhaps I am doing something wrong.

Thanks

---

### Post by cavalier911 on 2010-11-21
Look here: [https://bugs.launchpad.net/ubuntu/+bug/584339](https://bugs.launchpad.net/ubuntu/+bug/584339)

Thread #3 suggests a fix for black screen on startup by adding sisfb to /etc/modprobe or installing v86d package with synaptic

There is other information and links which may be helpful.

---

### Post by bizpeecocck on 2010-11-21
It seems lowering the screen resolution to 800x600 stops the problem. Though this isn't much of a fix, it's easier to switch to tty1 and back. Any ideas?

---

### Post by bizpeecocck on 2010-11-21
Hey, thanks for the link cavalier911. Adding sisfb to etc/modules did the trick. The only negative is that it made a mess of plymouth, but I can live with that. I'll probably disable it.

Again, thanks for your help.

---

