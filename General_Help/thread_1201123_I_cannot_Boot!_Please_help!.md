---
title: "I cannot Boot! Please help!"
date: 2009-06-30
forum: General Help
---

### Post by AINTEZ86 on 2009-06-30
I am having a problem simular to apperrently alot of people in here however none of the solutions anyone else provides seem to work. When I boot I get several error messages:

mount: mounting /dev/mapper/ubuntu-root on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootrag


Then when I have run a live cd and tried following several different advice I get the following:

sudo mkdir /media/root
sudo mount /dev/sda1 /media/root

mount: unknown filesystem type 'LVM2_member' (I have tried installing lvm2 and this command still doesn't work)

sudo fdisk /dev/sda1

The number of cylinders for this disk is set to 36449.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)
(It then comes up to a command prompt....I have been running this server for about a month before now without problems)

sudo e2fsck /dev/sda1

e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid , trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
efsck2 -b 8193 <device>

sudo e2fsck -b 8193 /dev/sda1

e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid , trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
efsck2 -b 8193 <device>


I am obviously in way over my head here because a) I am really new to ubuntu and b) I have no idea what in the world a super block is. 

Someone please help... if you need anymore info please let me know (I am going to need step by step direction).
 
 
 
(I am sorry this is a repost of another thread with a different title because no one responded to my last one so hopefully this will be better)

---

### Post by Don1500 on 2009-06-30
1st: You have not ever had this installation running? (You have no "work" you do not want to lose on the installation partition?)

2nd: If #1 is true, get the installation disk and re-install Ubuntu.
[INDENT]Make sure you put it in the correct partition[/INDENT]
[INDENT]Make sure the partition is formatted as ext3.[/INDENT]
[INDENT]Make sure you know the location (it should be hd0,1)[/INDENT]

---

### Post by AINTEZ86 on 2009-06-30
I have had it up and running for about a month so unfortunately I do have a good bit of 'work' on my server....its not a terrible amount but I would hate to lose it. I could redo it but I would lose a handful of files. Any other solutions?

---

### Post by AINTEZ86 on 2009-07-01
Does anyone else have any suggestions?

---

### Post by Sky Pixie on 2009-07-05
I, too, am over my head to offer the solution you want to hear.

I've installed Ubuntu 7.04, 8.04, and Arch to manually partitioned hard drives with LVM and LUKS.  I will not make assumptions to your partitioning methods, so I need some information.

1.  Which OS?
2.  How did you install the OS?
3.  Single hard drive?
4.  Does this hard drive have multiple operating systems?
5.  With which utility was the hard drive partitioned?
6.  What were the names and mount points of those partitions?

Thank you.

---

### Post by AINTEZ86 on 2009-07-05
Ok... I am going to try and answer your questions...if you need more information let me know....
1. OS- Ubuntu Server Edition
2. Installation- Downloaded the installation cd...(not sure what your asking but maybe that answers it)
3. Single Hard Drive- yes
4. Multiple OS- No
5. It was partioned during the installation...
6. I don't know...
I am sorry for my ignorance. I am pretty much a total newby and so if there is a way to find any other information that might help you help me I would be more then happy to try and figure it out. I just don't understand why it happened and how to recover it.

---

### Post by Sky Pixie on 2009-07-05
Did you manually partition the hard drive or did you let the installer partition the hard drive for you?

I ask because this
[quote=AINTEZ86]mount: mounting /dev/mapper/ubuntu-root on /root failed: Invalid argument[/quote]
tells me there is an LVM group named ubuntu and an LVM volume named root.  I can't imagine the Ubuntu installer using logical volumes by default because they add complexity to the installation.  I expect the Ubuntu installer to create primary partitions.

Try running the LiveCD again.

I think you will need to load the device-mapper kernel module before mounting the LVM partitions.  Sourced from [here](http://wiki.archlinux.org/index.php/LVM).
```
sudo modprobe dm_mod
```

List the partitions on sda:
```
sudo fdisk -l /dev/sda
```

List the logical volume groups:
```
sudo vgdisplay /dev/mapper/ubuntu
```

List the logical volumes:
```
sudo lvdisplay /dev/mapper/ubuntu
```

I'll wait for you to respond before I ask more questions.

---

### Post by AINTEZ86 on 2009-07-06
Here are the commands and there responses. I am sure I need to install the mod for the first one for them to work but I am sorry but I am not sure how to do that...I was atleast hopefully able to give you a little more information from the second one. Will check again tonight! Thanks for your willingness to try and help me. I think I let the installer partition it...but I might have done it manually...
 
 
sudo modprobe dm_mod
FATAL: Module dm_mod not found.
 
sudo fdisk -l /dev/sda
Disk /dev/sda: 300.0 GB 300069052419 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd957d957
Device Boot Start End Blocks Id System
/dev/sda1 * 1 36450 292784593+ 8e Linux LVM
/dev/sda2 36451 36481 249007+ 5 Extended
/dev/sda5 36541 36481 248976 83 Linux 
 
sudo vgdisplay /dev/mapper/ubuntu
sudo: vgdisplay: command not found
 
sudo lvdisplay /dev/mapper/ubuntu
sudo: lvdisplay: command not found

---

### Post by Sky Pixie on 2009-07-07
My bad.

Attach an ethernet cable to the computer, a backup medium, and boot the LiveCD.  From [here](http://www.linux-sxs.org/storage/fedora2ubuntu.html):

Install lvm2:
```
sudo apt-get install lvm2
```

Load the module:
```
sudo modprobe dm-mod
```

Check the file system:
```
sudo fdisk -l
```
Note the name given to the backup medium.

Enter the following if the sda1 partition is encrypted (I don't think it is):
```
sudo cryptsetup luksOpen /dev/sda1 sda1
```
Then enter the passphrase.

Scan the system for volume groups:
```
sudo vgscan
```
There is at least one volume called "ubuntu" on your system.

Activate the volume group(s):
```
sudo vgchange -ay ubuntu
```

Locate logical volumes:
```
sudo lvs
```

Continue if you recognize and/or can decipher the logical volumes.

Create a directory:
```
sudo mkdir /mnt/test0
```

Create another directory:
```
sudo mkdir /mnt/test1
```

Again:
```
sudo mkdir /mnt/test2
```

And again:
```
sudo mkdir /mnt/test3
```

Mount the logical volume from which to copy data (assumes the important logical volume is home):
```
sudo mount /dev/ubuntu/home /mnt/test0
```

Mount the backup medium:
```
sudo mount /dev/??? /mnt/test1
```

Change to the home directory to see which files and folders to backup:
```
cd /mnt/test0
```

Copy your files to some external medium:
```
cp /mnt/test0/??? /mnt/test1
```

Create additional directories and mount additional logical volumes as needed.

I must know the logical volumes before I can attempt to recover your system.

The following is to satisfy my curiosity.

I think sda5 is formatted as ext3.  Mount sda5:
```
mount -t ext3 /dev/sda5 /mnt/test2
```

Change to the /media directory which should have the contents of sda5:
```
cd /mnt/test2
```

List the contents of sda5:
```
ls
```

---

