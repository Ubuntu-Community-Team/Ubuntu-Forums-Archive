---
title: "Grey Screen"
date: 2010-05-13
forum: General Help
---

### Post by mc_tux on 2010-05-13
10.04 was working fine till one day I boot up, and there's a weird grey screen. I hear login sound, but nothing is displayed on the screen, it just goes grey with weird shapes and sometimes color stripes. Sort of like grey screen of death...
I thought I would recover my nvidia drivers, but I get the same grey screen when booting from Live CD also. Even from ubuntu recovery remix. Ubuntu Live CD launches, I get a menu, but when it starts to boot, grey screen again. I'm stucked. What could be the problem?

---

### Post by Grenage on 2010-05-13
Probably a bad graphics card, possibly a bad monitor or cable.

---

### Post by mc_tux on 2010-05-13
> **Grenage said:**
> Probably a bad graphics card, possibly a bad monitor or cable.
But I have a dual boot and everything works perfectly on Windows.
The grey screen seems to appear only when linux's kernel loads or something like that...

---

### Post by Grenage on 2010-05-13
That is very strange, I agree.  I would still recommend swapping the VGA cable out, if you have a spare one available.

Failing that - take out the graphics card, double check all connections between the card and the monitor.  This is real 'clutching at straws' stuff.

---

### Post by mc_tux on 2010-05-13
Thanks for your advices, but I wouldn't dare doing this on my laptop with integrated video card :) Again - it's VERY strage. Everything's perfect on Windows. Bios displays correct. A nice 10.04 Live CD menu appears. I choose to load Ubuntu. And then bah - that grey screen. Guess I will have to reinstall whole system.

---

### Post by Grenage on 2010-05-13
With it happening even on a live CD that was previously working, I would have suspect hardware.  No idea why it doesn't happen on Windows!

---

### Post by mc_tux on 2010-09-24
OK so after half a year I finally found the answer. It turns out to be a  bug or not a bug, related to nouveau+nvidia. To fix it, you have to add  nouveau.modset=0 when booting (in grub, press "e") or edit the file  /boot/grub/grub.

---

### Post by bak92 on 2011-03-26
Hey, I was having the same problem until I found this solution.  nouveau.modset=0 worked perfectly, and the Live CD actually works now.  I registered here just to tell you how thankful I am for your solution.  Thanks very much, sir!

---

