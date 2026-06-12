---
title: "Karmic initial load screen SUCKS! how to get rid of it?"
date: 2010-02-11
forum: General Help
---

### Post by onyxwolf on 2010-02-11
I hate Karmic's initial load screen. No load bar (even if its inaccurate you get used to how/where on the bar that your system will stall). Since my distro upgrade, 1 out of 3 times my system completely stalls, but it never happens when I boot into recovery mode, so I can't tell what process it hangs on. Does anyone know of a way to get rid of the load screen so we can see the shell loading at least?

---

### Post by NightwishFan on 2010-02-11
When you are at grub, edit the entry, scroll download to the linux kernel line, and delete: quiet splash

Press ctrl+X to boot. It will revert to default on the next boot.

---

### Post by onyxwolf on 2010-02-11
OK that didn't get rid of the boot screen, but it doesn't hang any when I do that and I think it actually boots a little faster. Any idea why that might be? Any idea how to permanently remove the quiet line from grub?

---

### Post by elliotn on 2010-02-11
Yes that boot screen suck big time, I prefere the old one.

---

### Post by onyxwolf on 2010-02-11
OK figured it out. I guess my hanging issue was due to the quiet line that was still in the legacy grub. I haven't upgraded my grub and don't plan on it. So, to get rid of that AND (most importantly the true solution to this post) to get rid of that stinking single icon / no progression boot screen:

gksudo gedit /boot/grub/menu.lst

Go toward the bottom and where it gives the booting lines remove the words quiet (this caused the hanging problem don't know why and would like to) and splash (kills the splash screen! YAY!!!)

The lines will look like:

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		a1a1(confidential hexadecimal key)a1a1
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=a1a1(confident hexadecimal key)a1a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

In the kernel line after root=uuid=blahblah ro I removed that quiet splash (not the last quiet so end result looked like:

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		a1a1(confidential hexadecimal key)a1a1
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=a1a1(confident hexadecimal key)a1a1 ro 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

Yet another way we can change Ubuntu to the WE want it. SO I'm not marking as solved, YET, so I can bring up another question we all want answered. We ALL know Karmic's boot screen is going to die by Lucid, BUT until then (or for those not wanting to change right away), how can we reinstall the boot splash from Jaunty? So we can have our beloved progression bar back! Any Ideas are welcome...

---

### Post by ironclaw on 2010-02-12
> **onyxwolf said:**
> In the kernel line after root=uuid=blahblah ro I removed that quiet splash (not the last quiet so end result looked like:

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        a1a1(confidential hexadecimal key)a1a1
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=a1a1(confident hexadecimal key)a1a1 ro 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

In menu.lst, you should also remove 'quiet' and 'splash' from the line beginning with
```
# defoptions=
```

This makes sure that the setting is kept for new kernels when update-grub is run.

---

### Post by onyxwolf on 2010-02-12
Thanks for the heads up!

---

### Post by onyxwolf on 2010-02-18
*Bump*

Anyone know how can we reinstall the boot splash from Jaunty? So we can have our beloved progression bar back! Any Ideas are welcome...

---

### Post by onyxwolf on 2010-02-22
Ok so I found out that the Usplash (I think is what its called) cannot be reinstalled without jacking with the kernel; however, you can install some kind of Xsplash replacement. My research was kinda dead end when it came to how though. Anyone have the link to a decent how to?

---

