---
title: "No Grub after an update"
date: 2012-06-29
forum: General Help
---

### Post by lael on 2012-06-29
I run Ubuntu 12.04 on my MacBookPro6,1 (17" 2010 model).

Today I saw that I had some updates waiting for me.  I applied them and finshed the day.  It looked like there was a kernel update and it asked me to 'restart to update'  I just shut down the machine at the end of the work day.

When I got home my machine wouldn't boot.  rEFIt boots and I can boot OSX, but my Linux option fails to load grub.  It just goes to a black screen with a white blinking cursor with no more machine response.  the caps-lock key indicator doesn't work and but the cursor is still blinking.

How do I go about trying to repair such an issue?

Partitions:
/dev/sda1 => fat32  (EFI partition)
/dev/sda2 => hfs+ Mac HD
/dev/sda3 => ext4 /boot
/dev/sda5 => ext4 Ubuntu 10.10
/dev/sda6 => ext4 Ubuntu 12.04
/dev/sda4 => swap

---

### Post by lael on 2012-06-30
Well, I got it fixed.  My guess was that grub somehow got corrupted.

A grub-install --force got me back in working condition from a LiveCD
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

---

