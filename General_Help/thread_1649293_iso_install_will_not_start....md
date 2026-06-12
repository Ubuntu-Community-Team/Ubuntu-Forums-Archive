---
title: "iso install will not start..."
date: 2010-12-20
forum: General Help
---

### Post by lemy on 2010-12-20
Hi, I have just bought a new machine and to explain my problem more clearly, I have attached a suppliers list. Essentially, there are two 1TB HD's installed, Disk0 is a multy boot with Windows7 & XP. Disc1 is empty, but partitioned at 500GB. Here, I intend to install Ubuntu 10.10. To that effect I have downloaded and burned the ISO from the Ubuntu download page. The disc fires up alright, but after searching for a few minutes displays the message:"Unable to find a medium containing a live file system." I have burned and tried the 32bit and the 64bit option since Win7 is the 64bit version. Alas, I was unsuccessful with each. When I look at the disc content I can see 9 folders named .disk, boot, casper, dists, install, isolinux, pics, pool and preseed. there are 4 files called 'autorun, md5sum, README.di and ubuntu. Finally a usb-creator and wubi. I should think this to be the complete distro, but is it?

---

### Post by Quackers on 2010-12-20
Welcome to UF.
Have you checked the md5SUM of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also exactly which version did you download please?

---

### Post by lemy on 2010-12-20
> **Quackers said:**
> Welcome to UF.
Have you checked the md5SUM of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also exactly which version did you download please?

Thanks Quakers, I have downloaded, burned and tried both versions, ie 32bit and 64bit since I am a Greenhorn at this and I thought it would make a difference. As for 'have you checked the md5SUM', I'm afraid, I don't know what you are talking about. Could you elaborate? Regards

---

### Post by efflandt on 2010-12-20
When you first boot the CD and see some graphics at the bottom, press any key, and in that menu there should be some selection to **Check disk** or similar that will check the CD against the md5sum.txt.  See if that comes up with any errors.

You might also want to boot that menu again and try letting **memtest86+** run for awhile to see if there is any incompatibility with the RAM they installed.  Sometimes a slight incompatibility will not immediately show up running Windows.  I had that issue when initially upgrading PC3200 RAM in an early Athlon64 in 2004.  WinXP appeared to run fine, but Linux would sometimes lock up and memtest86+ showed errors.  It was OCZ RAM bought on sale at Frys, but OCZ sent me RAM in exchange that they guaranteed would work, and it did with no errors.  I have since upgraded it with PNY RAM that works fine.

---

### Post by lemy on 2010-12-21
Hi and guess what, it worked. I don't know why, but it worked. Mind, with another iso and an earlier version (10.04) at that. I did the memtest86+, which came up ok, but when I attempted the Check disk utility, everything went black with only a blinking cursor. After having two goes at it, I booted the earlier version iso and hello, it installed correctly. I wonder why??
Anyway guys, thanks for your help, it's much appreciated. Regards W.L. ;)

---

