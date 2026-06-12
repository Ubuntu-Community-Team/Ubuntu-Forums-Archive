---
title: "Installing windows after Ubuntu"
date: 2011-10-18
forum: General Help
---

### Post by shad0w7 on 2011-10-18
I installed Ubuntu, on my laptop, and now I need to install windows due to some graphics development I need to do. What is the process that I need to follow? Will grub be installed too ?

---

### Post by Hylas de Niall on 2011-10-18
Windows will write over your grub bootloader with its own if you install it, which will mean a bit of work reinstalling grub to allow you back into Ubuntu.
There are folk on here who will be able to give detailed advice beyond that - i'm sure it's do-able - but i've only installed ubu alongside an existing windows (not the other way around), or done a clean wipe ;)

---

### Post by Leaf on 2011-10-18
see if one of these works for you, specifically the boot-repair option from the install CD or USB.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by varunendra on 2011-10-19
> **shad0w7 said:**
> I installed Ubuntu, on my laptop, and now I need to install windows due to some graphics development I need to do. What is the process that I need to follow? Will grub be installed too ?
Basic steps (assuming your hard drive currently has Linux partitions only):

[LIST=1]
[*]Boot with Ubuntu Live CD
[*]Using Gparted, resize/move first partition to create space for Windows. Make sure it is in the beginning of the drive.
[*]Create a primary partition in the emptied space and format it as NTFS
[*]Install windows in that partition
[*]Reboot into Ubuntu live session and reinstall grub as per this simple guide: [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)
[/LIST]
Please note that you can have at most 4 primary partitions in a drive. If you need more, you have to have one of them as 'extended partition' in which you can create more 'logical partitions'.

If having problems or need detailed instructions specific to you, please post output of ```
sudo fdisk -lu
```

---

