---
title: "Messed up X server, need help restoring"
date: 2010-06-17
forum: General Help
---

### Post by tylerwagler on 2010-06-17
I made some changes to the Nvidia Xserver settings and now I get no signal to my monitors.  I also have grub configured to only display the main ubuntu kernel and windows so there are no recovery options.  How do I restore Xserver to working or default values?

---

### Post by bodhi.zazen on 2010-06-17
run 

```
sudo nvidia-xconfig
```

If you can not get a terminal with ctrl-alt-F2 , reboot and edit your kernel line , just add either "text" of "1" at the end of the kernel line.

---

### Post by tylerwagler on 2010-06-17
can't seem to get a terminal with Crl+Alt+F2... how to I edit my kernel line?

---

### Post by wojox on 2010-06-17
Try Alt+F2 and enter gnome-terminal

---

### Post by tylerwagler on 2010-06-17
Alt+F2 doesn't do anything either.  All three of my monitors will go to powersave for a brief moment then come back on to a blank screen.  I hit 'e' in grub to edit whatever that is. It looks like this:

recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set f418c978-85...\
bbe
linux /boot/vmlinuz-2.6.32.22-generic-pae root=UUID=f418c...\
3e-a569... ro quiet splash
initrd /boot/initrd.img-2.6.32-22-generic-pae


where do i add 'text' ?

---

### Post by tylerwagler on 2010-06-17
SOLVED - replaced quiet splash with single reconfigured x automatically when it booted

---

### Post by WorMzy on 2010-06-17
> linux /boot/vmlinuz-2.6.32.22-generic-pae root=UUID=f418c...\
3e-a569... ro quiet splash

That's your kernel line. You can add what bodhi.zazen said to the end of that; although I'd recommend adding the word "single" instead. I don't know what "text" or "1" does, but single boots you into recovery mode, which lets you drop to a root shell (which is where you can either remove /etc/X11/xorg.conf, or run nvidia-xconfig.

EDIT: Guess I wasn't quick enough. Glad you got it sorted. :)

---

