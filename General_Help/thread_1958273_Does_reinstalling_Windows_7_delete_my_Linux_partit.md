---
title: "Does reinstalling Windows 7 delete my Linux partitions?"
date: 2012-04-13
forum: General Help
---

### Post by thunderpenguin on 2012-04-13
Hi

I am dualbooting Ubuntu 11.10 64 bit and Windows 7 Home Premium 32 bit.

Now I want to replace my Windows with Windows 7 Ultimate 64  bit.

Are my Linux partitions safe if I reinstall Windows 7 or do I need to backup the data on my Linux partitions?

---

### Post by sammiev on 2012-04-13
> **thunderpenguin said:**
> Hi

I am dualbooting Ubuntu 11.10 64 bit and Windows 7 Home Premium 32 bit.

Now I want to replace my Windows with Windows 7 Ultimate 64  bit.

Are my Linux partitions safe if I reinstall Windows 7 or do I need to backup the data on my Linux partitions?

You should be good to go but you will need to install grub2 again as windows will over write. Make sure you leave all partitions as is. Then again backups are always a must.

---

### Post by bodhi.zazen on 2012-04-13
You should always have a backup of your data regardless.

When installing windows, be very careful in specifying where you are installing it.

After you install windows, you will need to re-install grub

You can run boot repair from a live CD

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Or manually reinstall grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by thunderpenguin on 2012-04-14
Thank you.

I installed 7 Ultimate 64 bit and then booted my Ubuntu livecd and used Boot Repair to reinstall GRUB.

Now I am successfully dualbooting Ubuntu 11.10 and Windows 7 Ultimate 64 bit.

---

