---
title: "unable to boot ubuntu 10.10! help :("
date: 2011-01-17
forum: General Help
---

### Post by dupdupdup on 2011-01-17
i am unable to boot my ubuntu 10.10, 
This is the following i see upon booting up my ubuntu:

[B]Killed
Mount: mounting /dev on root/dev failed: No such file or directory
Mount: mounting /sys on root/sys failed: No such file or directory
Mount: mounting /proc on root/proc failed: No such file or directory
No init found. Try passing init=bootzary[/B]

and then it goes into busybox

As such i boot through my live cd.

I tried the following in terminal:

gre: command not found
ubuntu@ubuntu:~$ mount | grep sda6
ubuntu@ubuntu:~$ umount /dev/sda6
umount: /dev/sda6 is not mounted (according to mtab)
ubuntu@ubuntu:~$ sudo fsck
fsck from util-linux-ng 2.17.2
ubuntu@ubuntu:~$ sudo fsck.ext4 /dev/sda6
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?


Then i went on to try:

help ! i receive the follow message while double clicking my ## Filesystem.
**[SIZE=3]"Unable to mount ##GB Filesystem. A job is    pending on /dev/sd?#"[/SIZE]**

---

### Post by garvinrick4 on 2011-01-17
In the live Cd:
Open a terminal and download this script to desktop:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Then after it is on desktop run:
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```
will put a file called RESULTS on Desktop: Post it here:
After copy and pasted to this thread highlight whole thing and hit the
# in upper right hand corner of message box ans will put in nice little 
box to read out of. This will tell the story of your boot problems.

---

### Post by dupdupdup on 2011-01-17
> **garvinrick4 said:**
> In the live Cd:
Open a terminal and download this script to desktop:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Then after it is on desktop run:
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```will put a file called RESULTS on Desktop: Post it here:
After copy and pasted to this thread highlight whole thing and hit the
# in upper right hand corner of message box ans will put in nice little 
box to read out of. This will tell the story of your boot problems.

hi there thanks for your help but it loads indefinitely.

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 

it hangs here.
If it helps please see my first post i added something.

---

### Post by oldfred on 2011-01-17
Can you get it to at least show partition table?

sudo fdisk -lu

---

### Post by dupdupdup on 2011-01-17
> **oldfred said:**
> Can you get it to at least show partition table?

sudo fdisk -lu

yeah see below!

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    40965749    20482843+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    40965750   285153245   122093748    7  HPFS/NTFS
/dev/sda3       285155326   976771071   345807873    f  W95 Ext'd (LBA)
/dev/sda5       285155328   853339420   284092046+   7  HPFS/NTFS
/dev/sda6       853340160   971644927    59152384   83  Linux
/dev/sda7       971646976   976771071     2562048   82  Linux swap / Solaris

---

### Post by garvinrick4 on 2011-01-17
#I really do not know what is going on with linux install it seems to be in bit of
a mess. We can work on it in the Live CD.
#Lets get your Windows up and going and then see what is up in the linux and what
commands you were using before it went haywire.
# If you have your windows repair disk or installation disks use this link to get booting
A pretty simple task:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
#Now if you do not have a Windows disk use this below in Ubuntu live Cd in terminal
and internet connection:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Will say a error but ignore we only want the mbr part.
#Boot into your Windows on hard drive now.
#Once that is done get back on this thread and let us know and we will
get into your /root file system in Live CD and try and repair it using chroot command
and a few lines of code:
#You can start in Live Cd by running:
```
sudo e2fsck /dev/sda6
```It is like chkdsk in Windows
##Never run fsck while a drive is mounted
###If anyone else has better way to get this repair started chime in.

---

### Post by oldfred on 2011-01-17
Partition table looks ok to me. Others need to double check.


Did you have swap still mounted when you tried to run the file check. LiveCd's automount the swap partition which is in the extended so everything in the extended is seen as mounted. Use swapoff and try e2fsck again.

Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted,swap off if necessary, change sda6 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda6
if errors:
sudo e2fsck -f -y -v /dev/sda6
If that does not work:
List backup superblocks:
sudo dumpe2fs /dev/sda6 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda6
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by dupdupdup on 2011-01-18
Hi oldfred,

i used swapoff -a

and the commands you asked me to try all return the same message.

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
e2fsck: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?

So after the swap was off i went to Disk utility to check filesystem, it returned [B]Daemon is inhibited
[/B]
i used sudo killall udisks
then now when i go disk utility again it say **Filesystem is not cleaned**

---

### Post by oldfred on 2011-01-18
The only other time I have seen something similar, the user downloaded another distribution and that worked.  I do not remember what he downloaded but possibly Knoppix or Puppy? 

I found it used Slax liveCD and it seemed to work. The others may also. Just something about how the system loads.

[http://art.ubuntuforums.org/showthread.php?t=1627742](http://art.ubuntuforums.org/showthread.php?t=1627742)

---

### Post by dupdupdup on 2011-01-18
hi oldfred thanks for your help so far! i tried slax but i still cant fix it. some superblock issue. i decided to reinstall my ubuntu but it loads indefinitely when i try to install with the live cd. any idea or can i reformat my partition through windows? but there are 3 partitions. dont really want to mess it up. worried if i reformat the partition i would lose the grub boot menu and unable to boot to windows.

---

### Post by dupdupdup on 2011-01-18
hi oldfred thanks for your help so far! i tried slax but i still cant fix it. some superblock issue. i decided to reinstall my ubuntu but it loads indefinitely when i try to install with the live cd. any idea or can i reformat my partition through windows? but there are 3 partitions. dont really want to mess it up. worried if i reformat the partition i would lose the grub boot menu and unable to boot to windows.

---

### Post by garvinrick4 on 2011-01-18
> **dupdupdup said:**
> hi oldfred thanks for your help so far! i tried slax but i still cant fix it. some superblock issue. i decided to reinstall my ubuntu but it loads indefinitely when i try to install with the live cd. any idea or can i reformat my partition through windows? but there are 3 partitions. dont really want to mess it up. worried if i reformat the partition i would lose the grub boot menu and unable to boot to windows. 
#If you reformat partition will lose grub capabilities to boot. Grub looks into linux install for grub files. 
#When you install into same partition choose to reformat in ext4 it will reformat and reinstall grub to mbr you make sure you put grub in sda and mount point is /.
#Can reformat in install cd using Try Ubuntu and using gparted. Will have to reinstall
Windows bootloader then. See below:
# Do not know what you mean loads indefinitely:
#Here are some grub sites and gparted sites:
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/HowtoPartitio](https://help.ubuntu.com/community/HowtoPartitio)

---

