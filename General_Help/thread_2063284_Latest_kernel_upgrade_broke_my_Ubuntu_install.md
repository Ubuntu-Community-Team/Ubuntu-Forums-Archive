---
title: "Latest kernel upgrade broke my Ubuntu install"
date: 2012-09-26
forum: General Help
---

### Post by stepking2 on 2012-09-26
Today there were some kernel upgrades as well as some XORG upgrades. Installed them, and shut my computer down. When turning it on again, Ubuntu automaticly goes to terminal mode. So I log in and startx, but it just hangs there. The messages on the screen says is saying that it is starting and stopping this and that service, but it just hangs there.
When trying other kernels, it display that there were no input devices and displays found, but after following the wizard, the same thing happens as when starting x.
Starting LightDM does exactly the same thing.
What should I do?

OS: Ubuntu 12.04.1 64-bit.

---

### Post by cortman on 2012-09-26
Select the old kernel at the GRUB boot menu.
All the packages will still be upgraded, but you'll have your working kernel.

---

### Post by stepking2 on 2012-09-26
As mention in OP, I've tried running older kernels.

---

### Post by cortman on 2012-09-26
My mistake- I should have read better! Sorry. :redface:

What if you reinstall X?

```
sudo apt-get install xorg --reinstall
```

---

### Post by stepking2 on 2012-09-27
No problem ;)

But reinstall xorg did not work, it does exactly the same thing as before.

I also saw another thread where there were some people who had the same problem as I.

EDIT: Got it fixed. 
Luckly I had the AMD CCC 12.8 installer in my documents, so reinstalling my drivers fixed it.

---

### Post by danaross on 2012-09-27
>EDIT: Got it fixed. 
Luckly I had the AMD CCC 12.8 installer in my documents, so reinstalling my drivers fixed it.<

How did you do that? I have the same problem. 
dana

---

### Post by dino99 on 2012-09-27
This is a borked xorg installation (missing some package(s)).
Repair it via chroot from a livecd or liveusb (the same as the installed one)

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

... or redo a fresh install over that borked one.

---

### Post by danaross on 2012-09-27
thank you.

---

### Post by stepking2 on 2012-09-28
> **danaross said:**
> >EDIT: Got it fixed. 
Luckly I had the AMD CCC 12.8 installer in my documents, so reinstalling my drivers fixed it.<

How did you do that? I have the same problem. 
dana

If you have a discreet AMD card, then download the installer to a USB stick, cd over to the USB stick, sh the installer as root and follow the on screen instructions.

---

