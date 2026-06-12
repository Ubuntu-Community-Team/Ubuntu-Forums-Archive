---
title: "logon crash"
date: 2011-07-16
forum: General Help
---

### Post by bacdad on 2011-07-16
[Hello, Ubuntu/Linux Newbie]("http://ubuntuforums.org/showthread.php?t=1805587")

hello all
a couple of days ago i was logging in and cat landed on keys,blank screen, mouse not moving:(
finally i pulled battery to reboot and got (grub rescue>) so i looked up some comands like (dump, sda 01, chroot /dev/sda1, chroot/dev/sda1, mount /dev/sda1) about 10 of them

unknown comand " chroot" " grub"

help in repair  i have limited time on this computer to make repairs:confused:

---

### Post by ajgreeny on 2011-07-16
Boot to a live CD/USB, open a terminal and run ```
sudo e2fsck /dev/sdx#
``` where sdx# is the root partition for your ubuntu install.  By doing this the damaged filesystem may be repaired, and allow you to login again.

Good luck!

---

