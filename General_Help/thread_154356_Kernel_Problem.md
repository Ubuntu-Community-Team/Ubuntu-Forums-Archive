---
title: "Kernel Problem"
date: 2006-04-02
forum: General Help
---

### Post by deboring21 on 2006-04-02
I tried to install the newest version of the kernel for my system (linux-image-686-smp with the latest version of 2.6.12.16.1). After I reboot my system, I get an error message during the boot up ](*,) . It saws something about an error with X Server. I reboot it again and go back to the old kernel and it works just fine. I need the new kernel for my dual proc's to work right. Has anyone else had a problem or know of any fixes for it?
-Ryan

---

### Post by nanotube on 2006-04-02
can you give any more details on what kind of error with x server it has? that might be helful in figuring out a solution...

---

### Post by Sutekh on 2006-04-03
[QUOTE=deboring21]I tried to install the newest version of the kernel for my system (linux-image-686-smp with the latest version of 2.6.12.16.1). After I reboot my system, I get an error message during the boot up ](*,) . It saws something about an error with X Server. I reboot it again and go back to the old kernel and it works just fine. I need the new kernel for my dual proc's to work right. Has anyone else had a problem or know of any fixes for it?
-Ryan[/QUOTE]
Had you previously installed official/custom NVIDIA/ATI video drivers?

If so you will need to install them again using the new kernel. This is because the official drivers load their own driver module into the kernel.  So new kernel, new module.

I assume that when you boot the new kernel you are dropped to the command line?  You can re-install the official drivers from there.

If you'd prefer to do most of it from the desktop, use this code
```
sudo nano /etc/X11/xorg.conf
```
Which will open a simple editor.  Look for this section.
```
Section "Device"
```
and change the line that contains
```
Driver "some driver"
```
To
```
Driver "nv"
```
For NVIDIA cards, or
```
Driver "vesa"
```
For ATI cards.

Save the file (Ctrl+O) and exit (Ctrl+X) and the restart the display manager with
```
sudo /etc/init.d/gdm restart
```
You should get back into GNOME, with the open source video drivers.

Then you can re-install the drivers you had in the old kernel.

---

### Post by deboring21 on 2006-04-03
So how do I install the drivers again? I think that I installed them using Automatix or something, not totally sure though...

---

### Post by Clopy on 2006-04-03
just follow this guide:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by Sutekh on 2006-04-03
[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://ubuntuforums.org/showthread.php?t=75074")

 - Method 1 is dead easy (same as wiki link and the way Automatix does them) and install the drivers in the restricted part of the Ubuntu repositories.  The drivers are version v7667. 

 - Method 2 is a little harder and more involved, but still doable.  It will install the official drivers from NVIDIA's website.  You can install any version of the drivers.  This is useful for some cards which don't seem to work with the latest drivers.  The latest drivers are v8178.

---

