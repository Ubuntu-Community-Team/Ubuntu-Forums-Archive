---
title: "Installing 12.04 from USB"
date: 2012-04-26
forum: General Help
---

### Post by Quarkrad on 2012-04-26
I've just downloaded 12.04 and installed onto a USB stick.  I did manual install re-formatting my existing sda2 ext4 (was ubuntu 10.10) partition.  The installer finds winxp on sda1 and presents me with two options to include sda1 in grub. Whatever sda1 option I choose when the install of 12.04 finishes and the pc reboots I get a blank screen with

error: file not found, 
Entering rescue mode, 
grub>rescue

Pre 12.04 I gone through this install process quite a few times and am familiar with the install process.  As I have tried installing twice now (because the installer gives me two options for sda1) and both have failed.  Is there anything I can do re the flashing cursor re grub?  I've just tried it a 3rd time - this time not choosing sda1 - but it still comes up with a flashing cursor grub>rescue.  Any suggestions?

---

### Post by oldfred on 2012-04-26
When you say options for sda1 are you talking mounting or installing grub2's boot loader? If you install the grub2 boot loader to sda1, if corrupts the Windows boot loader and leaves the old boot loader in sda which then may give the error.

To confirm what is where run the boot info script and post the link.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Or this may let you directly boot:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Quarkrad on 2012-04-27
Thanks - got it sorted.  I'm not sure boot-repair is available now - I reinstalled grub in the end via terminal commands.  Some google pages say boot-repair is no longer available.

---

### Post by oldfred on 2012-04-27
Glad you got it working.

Boot-Repair is there and works well for many.

---

