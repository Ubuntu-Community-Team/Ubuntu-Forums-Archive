---
title: "Cannot mount root partition"
date: 2010-01-13
forum: General Help
---

### Post by punchdrunkgrunt on 2010-01-13
Aargh!
When I try to boot I get this error message:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the systemwait long enough?)
  - Check root= (did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/c946b41f-2f8f-4a28-8478-11a50d6fc0e8 does not exist. Dropping to a shell!

Booting from my 9.10beta livecd sudo fdisk -lu shows my root partition (sda5) but  blkid doesn't, and there's no way to mount it.

I know similar questions have been posted before but they all involve using fsck or e2fsck, which don't work with my ext4 filesystem.

FYI Acer Aspire 7535G Kubuntu 9.10 AMD64

TIA

---

### Post by michy99 on 2010-01-13
Did you run blkid as root?```
sudo blkid
```

---

### Post by Leppie on 2010-01-13
is this a recent livecd? ext4 is the default filesystem for karmic, so fsck should support it as well. otherwise you can always try to install some packages:
```
sudo apt-get install e2fslibs e2fsprogs
```

---

### Post by punchdrunkgrunt on 2010-01-13
I'm using my 9.10 beta livecd, I think it's got an older version of fsck on it.
Using the live cd I've managed to mount my root partition and /etc/fstab looks fine.
Seems like some other file in the boot sequence is messed up, but I've no idea which one.
To be continued...

---

### Post by drs305 on 2010-01-13
If you are using Grub 2, an easy way to see if it's just the UUID that is giving you the problem is to edit the menu entry. If you don't see the menu, hold down the SHIFT key during boot. 

Once you see the menu, highlight the entry, press "e" to edit it, and remove the "search" line entirely and then in the "linux" line change the root=UUID=XXXXXXXx to root=/dev/sdXY, with XY being your drive and partition (so sda1, sda5, sdb1, etc). If you have to guess, installs are normally on sda1 for ubuntu only and sda5 for windows/linux default installs. Don't press ENTER - use the arrow keys to move the cursor. Press CTRL-x to boot afetr making the changes.

If you can get into Ubuntu this way let us know and we can tell you how to fix your menu and fstab if necessary since these changes won't be permanent.

---

### Post by punchdrunkgrunt on 2010-01-13
Yay.
That worked! Thanks.
Do I now need to punish some misbehaving files to stop it happening again?

---

### Post by drs305 on 2010-01-13
> **punchdrunkgrunt said:**
> Yay.
That worked! Thanks.
Do I now need to punish some misbehaving files to stop it happening again?

Your Grub 2 UUIDs are incorrect for some reason.

If you are in your normal Ubuntu install, run these commands:
```

sudo update-grub
sudo blkid -c /dev/null
gksu gedit /boot/grub/grub.cfg  /etc/fstab

```

Now compare the UUIDs from the *blkid* command for your system partition with what is listed in grub.cfg and fstab.
They should now match - update-grub must have found the correct system UUIDs and replaced them in Grub 2.

If for some reason your grub.cfg and blkid UUIDs still do not match, we can change the UUID of your system partition to match what is in grub, but first we need to make sure that UUID doesn't exist elsewhere on your computer and that you are looking at the correct grub.cfg. So if they don't match, post "sudo fdisk -l" and "sudo blkid" results, or better yet, provide the results from the boot info script:
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")


Since it booted correctly, /etc/fstab should be correct but you should probably check the / listing anyway just to be sure.

---

