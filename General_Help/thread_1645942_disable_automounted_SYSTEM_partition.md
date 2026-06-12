---
title: "disable automounted SYSTEM partition"
date: 2010-12-15
forum: General Help
---

### Post by ryu kun on 2010-12-15
Hi !

I have Windows 7 on the computer along with Ubuntu 10.10. There is a drive named "SYSTEM" in my Places menu. It's in /dev/sda1, its mount point /media/SYSTEM and it carries "boot" flag according to Gparted. 

I don't know if it's safe to delete this partition (its size is 198 mb, 22 mb is used). If it's not safe, I want to disable this drive's automount. 

There isn't any entry regarding that in /etc/fstab file.  

How can I manage to disable its automount?

---

### Post by flyingbear on 2010-12-15
I strongly recommend NOT to delete this partition. It's reserved for your Windows OS. Windows XP takes only 8MB but Vista and 7 take 200. If you don't want to mount this partition just edit your /etc/fstab file. ```
sudo vim /etc/fstab
```There should be something like this```
/dev/sda1 /media/SYSTEM ntfs-3g ... 
``` Just remove it or comment it (place # as a first symbol in the line).

---

### Post by ryu kun on 2010-12-15
Thanks for your reply. It is strangely not listed in /etc/fstab file...

---

### Post by Linyx on 2010-12-15
> **ryu kun said:**
> Thanks for your reply. It is strangely not listed in /etc/fstab file...

[SIZE="2"]Can you please paste your FSTAB here...[/SIZE]

---

### Post by ryu kun on 2010-12-15
Here it is:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=xxx /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=xxx /home           ext4    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=xxx /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=xxx none            swap    sw              0       0

---

### Post by Linyx on 2010-12-15
[SIZE="2"]how you have manage your FSTAB,...? have you used any tool for Auto-mounting NTFS-Drives...or you had Edited your FSTAB ***manually***

why your uuid=xxx ???Its strange for me....Moreover , the drive which you are talking about is NTFS/Ext-3/4....?[/SIZE]

---

### Post by ryu kun on 2010-12-15
I just replaced my UUID's manually with "xxx" before copying them here. Other than that I didnt made any change.

I use Truecrypt to mount encrypted drives but I doubt if this is related to my "SYSTEM problem".

Another detail: Even unmount "SYSTEM" I still can see it in Places menu. Annoying.

---

### Post by Linyx on 2010-12-15
> **ryu kun said:**
> I just replaced my UUID's manually with "xxx" before copying them here. Other than that I didnt made any change.

I use Truecrypt to mount encrypted drives but I doubt if this is related to my "SYSTEM problem".

Another detail: Even unmount "SYSTEM" I still can see it in Places menu. Annoying.

[SIZE="2"]i don't know what this uuid=xxx means...

But i think that this is because of your "true-crypt", and you didn't answer my question...is that system is ntfs/ext...or what...?[/SIZE]

---

### Post by ryu kun on 2010-12-15
Sorry, I forgot to answer your question. It's a NTFS partition.

---

### Post by ryu kun on 2010-12-15
I don't think it's related with Truecrypt. It's still there even when I do not use Truecrypt at all.

---

### Post by Linyx on 2010-12-15
[SIZE="2"]can you let us know about the output of "sudo blkid"[/SIZE]

---

### Post by ryu kun on 2010-12-15
Here it is:

> /dev/sda1: LABEL="SYSTEM" UUID="xxx" TYPE="ntfs" 
/dev/sda2: UUID="xxx" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="xxx" TYPE="ntfs" 
/dev/sda5: UUID="xxx" TYPE="ext4" 
/dev/sda6: UUID="xxx" TYPE="ext4" 
/dev/sda7: UUID="xxx" TYPE="swap" 
/dev/sdc1: LABEL="xxx" UUID="xxx" TYPE="ntfs" 
/dev/mapper/truecrypt1: UUID="xxx" TYPE="ext4"

---

### Post by Linyx on 2010-12-15
[SIZE="2"]Its Completly ***Strange*** for me that why it is Auto-mounting at Boot on your OS as its not listed in FSTAB....[/SIZE]
[SIZE="2"]Can you explain a little bit about UUID=xxx, my UUID=some aplphabits & digits....[/SIZE]

Edit:- In places menu, if Drives are mounted or not,it doesn't make drives not appear their.....Drives installed on your PC must shows in your Places menu...

Any how, their are a ***methods*** of howto **remove/Hide** it from places....

---

### Post by efflandt on 2010-12-15
That Windows SYSTEM partition should not auto mount unless you click on it in Places, so the **mount** command in a terminal should not show it mounted otherwise.

So your question really should not really be whether to "delete that partition", but "**how to have a partition not show up in Places**".   Places uses Nautilus, and you can add/delete things from the lower  left pane (below separation bar), but upper left pane finds partitions  automatically, so not sure how to hide partitions there if they are not  marked as hidden partitions on the drive.  I don't know if deleting it  from that list would stick next boot.

My Places does not show my Dell RECOVERY partition sda2 where Win7 boots  from, even though it is the same ID 7 HPFS/NTFS as sda3 where Win7  actually runs from as C:.  But it does list "41 MB Filesystem" which is  sda1 that fdisk lists as ID de Dell Utility.  So if we can figure this  out, it would be nice to have that NOT show up in my Places.

That all has nothing to do with grub2, which finds my Win7 boot loader  on sda2 with update-grub even though sda2 is not listed in Places.

---

### Post by Linyx on 2010-12-15
[SIZE="2"]You can hide that Partiton from places Menu, for that you just have to edit FSTAB & hide-partitions.rules > [http://ubuntuforums.org/showthread.php?t=1642958&page=6]("http://ubuntuforums.org/showthread.php?t=1642958&page=6")[/SIZE]

---

### Post by tad1073 on 2010-12-15
> **Linyx said:**
> [SIZE=2]i don't know what this uuid=xxx means...

But i think that this is because of your "true-crypt", and you didn't answer my question...is that system is ntfs/ext...or what...?[/SIZE]

> **ryu kun said:**
> I just replaced my UUID's manually with "xxx"  before copying them here. Other than that I didnt made any  change.

He replaced th UUID's of the disks with xxx for security reasons.

---

### Post by Linyx on 2010-12-15
> **tad1073 said:**
> He replaced th UUID's of the disks with xxx for security reasons.

[SIZE="2"]well thanks for that, but how can i do this..?[/SIZE]

---

### Post by ryu kun on 2010-12-15
I messed up my partition table by using following command:

> sudo blkid -c /dev/sda1

It made SYSTEM partition disappear from Places, and in Gparted that partition appeared with an error icon. 

I used testdisk to recover the partition and restored backup boot sector, but it was a big mistake because after that my partition table messed up. All my ext4 partitions disappeared and I cannot boot Windows either. I am trying to rescue now :confused:

---

### Post by tad1073 on 2010-12-15
> **Linyx said:**
> [SIZE=2]well thanks for that, but how can i do this..?[/SIZE]

He just edited his fstab to post on the forums, his uuid's aren't xxx in the file that lives in /etc

---

### Post by ryu kun on 2010-12-16
I've found a solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1305383&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1305383&page=2)

I edited "/etc/udev/rules.d/hide-partitions.rules"

> 
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

# Floppy Drive which should not display
KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{UDISKS_PRESENTATION_HIDE}="1"

# Partition sda2 that we want to hide from gnome
KERNEL=="sda1", ENV{UDISKS_PRESENTATION_HIDE}="1"

LABEL="hide_partitions_end"

It works on Ubuntu 10.10.

---

