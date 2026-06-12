---
title: "How does Nautilus unmount/poweroff?"
date: 2012-08-22
forum: General Help
---

### Post by Nick8 on 2012-08-22
Hello, this should be a simple question. I was wondering how Nautilus manages to power off an external hard drive as well as unmounting, it after selecting 'Safely Remove Drive'. I've noticed that no other Linux file manager can do this, and neither can Windows Explorer on Windows 7. All they can do is unmount the drive without powering it off.

I've read that it can be done via the command line using hdparm or sg3_utils, but I have neither of those installed, and Naultilus is still able to do it.

Thank you in advance for you replies.

---

### Post by dcstar on 2012-08-23
> **Nick8 said:**
> Hello, this should be a simple question. I was wondering how Nautilus manages to power off an external hard drive as well as unmounting, it after selecting 'Safely Remove Drive'. I've noticed that no other Linux file manager can do this, and neither can Windows Explorer on Windows 7. All they can do is unmount the drive without powering it off.

I've read that it can be done via the command line using hdparm or sg3_utils, but I have neither of those installed, and Naultilus is still able to do it.

Thank you in advance for you replies.

The Windows "Remove USB devices" function does exactly that.

It is just background commands to the hardware.

---

### Post by Nick8 on 2012-08-23
> **dcstar said:**
> The Windows "Remove USB devices" function does exactly that.

It is just background commands to the hardware.

It's funny you say that because on my Windows 7 Computer, the 'Remove USB devices' function does NOT power off my USB hard drive or my flash drive. Using Nautilus, the LED on each one goes off, so I know it's powered off.

---

### Post by Nick8 on 2012-12-16
I've worked this out myself, in case anyone is interested.

Nautilus unmounts an external drive by doing 'udisks --unmount'; and it powers off the drive by doing 'udisks --detach'.

However Naultilus no longer gives the option to power off external drives (i.e. 'safely remove drive'). Just another GNOME 3 regression. *SIGH*

---

