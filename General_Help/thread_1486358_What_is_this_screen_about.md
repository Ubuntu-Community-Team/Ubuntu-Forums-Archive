---
title: "What is this screen about?"
date: 2010-05-17
forum: General Help
---

### Post by toxic9813 on 2010-05-17
I get this screen when I try to boot Ubuntu 10.04
What do I do here to get to my computer?

(sorry for flash)

---

### Post by toxic9813 on 2010-05-17
Bump.

---

### Post by efflandt on 2010-05-17
See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and scroll down to **Command Line and Rescue Mode**.  You may want to print that to a PDF file or portions of it, so you can refer to it.  That gives commands you can try using to find and boot Linux.

Apparently grub2 is able to find some of its files, so you at least get the **grub>** prompt.  But something may not be configured correctly.  Never edit /boot/grub/grub.cfg, instead edit /etc/default/grub or files in /etc/grub.d/ and then **sudo update-grub** from that system.

I have a USB drive with 10.04 LTS that boots fine on 2 laptops, but fails to boot on my desktop with "error: unknown filesystem" and drops to a much more limited **grub rescue>** prompt.  grub rescue is unable to read any partition on the USB drive, and a regular grub(2) prompt from my main drive is able to read the ntfs partition on that drive, but not the ext3 partition containing Linux.  But that may be a BIOS issue, because I eventually got that desktop to boot 10.04 from a 160 GB USB drive, and it boots 10.04 from its main 200 GB hard drive, but it refuses to boot 10.04 from a 500 GB USB drive.

If you think you may have a video issue (since that changed in 10.04) you might try removing the **splash** parameter and using **nomodeset** instead. For release notes see [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

---

### Post by toxic9813 on 2010-05-17
I tried the first link, the recovery thing... in the X Y thing you have to put something else in right? I don't know what to put in.

---

