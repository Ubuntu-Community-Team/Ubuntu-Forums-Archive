---
title: "Installed WinXP, not able to boot it with GRUB"
date: 2006-04-22
forum: General Help
---

### Post by JanZ on 2006-04-22
Hello folks,

seems like I have an issue here. I had SuSE 9.2 installed on /media/hda3 (reiserfs) and Breezy on hda1 (ext2). I wasn't using SuSE anyway and since I needed to install some Windows-supported software (Wine wasn't a solution this time), I installed XP on the SuSE partition (during the installation, reformatted it to be NTFS). 
Well, installing Windows AFTER installing Linux (as I mentioned, Breezy was already there) makes the
system boot only Windows. So I put in the Breezy installation CD and in the rescue mode installed GRUB:

```
grub-install /dev/hda1
```

This way I got back the GRUB bootloader with SuSE still figuring there. No option to boot Windows of course. Additionally, I get the following messages when booting Breezy:

```
* Checking all file systems ...
reiserfs-open: the reiserfs superblock cannot be found on /dev/hda3.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is valid and it really contains a reiserfs partition, then the superblock 
is corrupted and you need to run this utility with --rebuild-sb.
									
                                                                            [fail]

* fsck failed. Please repair manually.

* CONTROL-D will exit from this shell and continue system startup.

root@(none):~# *(hitting Ctrl+D here)*

        Mounting local filesystems
mount: mount point /media/hda3 does not exist
                                                                             [fail]
```

So now I'd need tips to solve the following problems:

1) How to get GRUB to boot WinXP and
2) How to get rid of these messages during the Breezy boot (Breezy boots up succesfully, but the messages are annoying).

I would be more than happy to avoid any further OS-reinstallations. :( 


Jan

---

### Post by Irony on 2006-04-22
Add an entry to the end of your;

[PHP]sudo gedit /boot/grub/menu.lst[/PHP]

[PHP]# This entry automatically added by yourself for a non-linux OS
# on /dev/hda1
title		XP Home SP2, hda1
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/PHP]

Change the *root* entry to whatever your partition is, if its hda3 for XP the put (hd0,2) - that should boot XP and get rid of the message. The *title* entry you can name it as whatever you like.

---

