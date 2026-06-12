---
title: "Installing Kubuntu Results in Brrken Grub"
date: 2011-08-25
forum: General Help
---

### Post by MegaLoler on 2011-08-25
I have tried to install Kubuntu twice on my Mac mini but each time I try to boot onto the new installation I am greeted by a totally broken grub prompt.  No commands at all work, not even reboot.

I have tried to restore grub but:
-using find /boot/grub/stage1 fails with Error 15: File not found
-using set root=(hd1,4)    ls /boot    fails saying it can't find it.

I have it installed on both my internal drive and my external drive.  Both have their own dedicated ext4 partition (next to an hfs+ partition) that I set up within the Kubuntu installer.

I have installed Ubuntu on this machine previously with no problems like this.

Can anyone help me?  I really want to get Kubuntu working!  Thanks.

---

### Post by MegaLoler on 2011-08-25
Bump

---

