---
title: "lvm volume shown in test disk but not the partitions"
date: 2011-01-29
forum: General Help
---

### Post by beopen on 2011-01-29
i have 2 hdd
hdd1 = windows xp
hdd2[500gb] = only ubuntu 10.04[ partition as under
         [250 mb= boot 
   lvm of 300gb containing 
          / = 10gb
        home = 289gb  & swap =1gb
lvm was created in 2nd partition type primary.

yesterday i had deleted all partitions in the first drive of windows only from ubuntu disk utility.
today i went to install windows and the partition space was shown as [139gb] , i thought this is the first hard disk. But my guess is windows must have taken the free space on my home partition inside lvm[ 150gb which roughly translates to 139 GiB. 
SO first i deleted the whole partition of 139gb which was shown different in unallocated space as a slight less figure and then i created a 30gb partition on that space shown and went ahead, windows post creation again showed 139gb and then gave a message on next window that partition does not contain data to install windows xp. Strange i thought, this becoz next screen before the format partition as ntfs is all to be shown.
Then i just felt something fishy and rebooted and then ubuntu of 2nd hdd is not booting.


i ran test disk from gparted live cd and i find td recovered the boot drive but not the 2nd **primary** partition in which lvm [root,home,swap] is created. It shows the lvm as 279gb. But not the 3 logical partitions inside it.
Now when i boot post the grub menu i get the following message

------------------------
gave up waiting for root device. common problems
---boot args (cat/proc/cmdline)
--- check rootdelay=(did the system wait long enough?)
--- check root = ( did the system wait for the right device?)
---missing modules (cat/proc/modules ; ls /dev)
ALERT ! /dev/mapper/VOLCOW-ROOT does not exist.Dropping to a shell !
BusyBox v 1.13.3(ubuntu x x x x some version no) built-in-shell (ash)
Enter 'help' for a list of built-in-commands.

--------------------------

pls help me what to do now.........
This disk contains all my data and the first drive was also wiped out full. test disk is not able to get anything on that windows drive.........

---

### Post by srs5694 on 2011-01-29
First, Windows doesn't know Linux's LVM from a frog in a pond, so there's no way Windows would have detected and attempted to use free space inside the LVM. Windows might conceivably have deleted the LVM partition (like a frog in a road, with Windows being an oncoming 18-wheeler), but Windows wouldn't attempt to use data within the LVM.

Second, LVMs don't contain logical partitions; they contain logical volumes. This may sound like a trivial semantic distinction, but it's not; partitions consist of contiguous sets of sectors, whereas logical volumes may be discontiguous. This can make it harder for a tool like TestDisk to properly recover a deleted logical volume.

Third, if Windows trashed and overwrote your LVM partition, TestDisk might not be able to recover anything inside it, since the critical Linux filesystem data might now be missing.

Don't give up, though. Boot a Linux emergency disc (such as an Ubuntu install disc in live CD mode, [PartedMagic,](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org) Open a Terminal window and run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) (you'll need to download it, of course). It should produce a file called RESULTS.txt. Post that file here, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. This will tell us how your partitions are laid out and what your boot configuration is. We may ask you to run additional commands for diagnostic purposes.

---

