---
title: "Remove Mint from Triple boot laptop (XP, Ubuntu 9.04, Mint Gloria)"
date: 2009-10-26
forum: General Help
---

### Post by Rainbow Road on 2009-10-26
I have been running the above O/S but now want to remove Mint and intend to replace Ubuntu with 9.10 when it is released.

The grub is from the Mint installation - how do I restore the Ubuntu grub and delete Mint. I have considered deleting the Mint partition with Gparted but presume this would cause computer not to boot as using the Mint grub.

```
fdisk -l     (Mint SDA7; XP SDA1; Ubuntu SDA5 & Shared NTFS Folder SDA9)
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7108f6c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5227    41985846    7  HPFS/NTFS
/dev/sda3            5228       19457   114302475    5  Extended
/dev/sda5            5419       10419    40170532+  83  Linux
/dev/sda6            5228        5418     1534144+  82  Linux swap / Solaris
/dev/sda7           10420       15273    38989723+  83  Linux
/dev/sda8           15274       15550     2224971   82  Linux swap / Solaris
/dev/sda9           15551       19457    31382946    7  HPFS/NTFS

```

Anyone got any advice or recommendations for removing.

---

### Post by Meskarune on 2009-10-26
you can use gparted to just reformate and hence delete linux mint. The follow the procedure here:
[URL="http://ubuntuforums.org/showthread.php?t=224351"]
http://ubuntuforums.org/showthread.php?t=224351[/URL]

---

### Post by oldfred on 2009-10-26
Just reinstall grub and tell it to point to the Ubuntu install rather than the mint install. You do not have to use the liveCd if you are in mint or ubuntu. You need to know which partition is ubuntu as opposed to mint and then when you use the find command in grub choose the ubuntu partition for the root command.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,4)
root (hd0,4) #use the numbers from the previous command
setup (hd0)

---

### Post by Rainbow Road on 2009-10-26
> **oldfred said:**
> Just reinstall grub and tell it to point to the Ubuntu install rather than the mint install. You do not have to use the liveCd if you are in mint or ubuntu. You need to know which partition is ubuntu as opposed to mint and then when you use the find command in grub choose the ubuntu partition for the root command.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,4)
root (hd0,4) #use the numbers from the previous command
setup (hd0)

When I have done find /boot/grub/stage1 I get:

grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,6)

grub> 

As mentioned in my previous post I know Ubuntu is on sda5 (would that be hd0,4 and Mint on sda7 be hd0,6)

So would the next step be:
root (hd0,4) #to restore Ubuntu grub; and then
setup (hd0)

---

### Post by oldfred on 2009-10-26
Should work as long as your Ubuntu still boots. It will give error message if it cannot find at least the files it needs to boot.

---

### Post by Rainbow Road on 2009-10-26
It worked, thanks very much.

---

