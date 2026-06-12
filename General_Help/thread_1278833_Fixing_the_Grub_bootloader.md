---
title: "Fixing the Grub bootloader"
date: 2009-09-30
forum: General Help
---

### Post by sir.jeyhmis on 2009-09-30
Hello Ubuntu gurus!

I've just begun using Jaunty Jackalope, so I will need some fairly systematic help, please!

Right now I am attempting to dual boot Vista and Jaunty.  I've installed the Grub bootloader and have had no actual Ubuntu problems yet, which is nice.

My problem is to do with Grub, as I, the human, have screwed things up.

My intention was to reorganize and modify the list of options and shorten the count down value.  In the terminal within Ubuntu, I was able to modify the menu.lst file enough to accomplish a few things.

The list in Grub used to load up this way:

Ubuntu
A series of Ubuntu modules
A separator labeled something like "Other Operating Systems"
Windows Vista
Dell Utility Partition (or something like)

In the Terminal in Ubuntu, I rearranged the list and then "commented out" the titles of the options I didn't want to see in the list (only the titles, unfortunately).

Grub now loads this way:

Windows Vista
Ubuntu

Windows Vista loads just fine, which is helpful.  Ubuntu, however, does not.  Upon editing the Ubuntu option in Grub, all of the coding for all of the other options appears as a collected list, ending with the Dell Utility Partition option.
Upon selecting Ubuntu to load, Grub attempts to boot each option, failing each time, until it successfully boots the Dell Utility Partition.
Because Ubuntu will not boot, the Terminal is no longer accessible.

As far as I can tell, all I need is access to the Ubuntu Terminal, or else a way to reinstall the Terminal from the LiveCD.

How can I reinstall Grub from the CD?  Or how can I access the Ubuntu terminal?

Thanks!

---

### Post by nikhilk on 2009-09-30
You could boot from a live-CD and then fixup your messed up /boot/grub/menu.lst file.

For starters, boot via a live-CD and post output of ```
sudo fdisk -l
```

---

### Post by sir.jeyhmis on 2009-09-30
So I should boot from the CD, open the Terminal, and type "sudo fdisk -1"

This will let me edit the /boot/grub/menu.lst file?

---

### Post by rbc on 2009-09-30
sudo fdisk –l 
This will display all the partitions, and file system types, on the hard drives. The results of that command will help determine what your menu.lst should be. By the way, the character after the hyphen in that command is a lower case L, not the number 1

---

### Post by sir.jeyhmis on 2009-09-30
Ok, so in the LiveCD terminal, I can use the command "sudo fdisk-l" to find the partitions and file types on my hard drive.
What does this information help me with?  Do I need the "sudo fdisk-l" info to find the menu.lst file?

I need to edit the menu.lst file or else replace that screwed up file with the CD's so I can start over.  How do I edit or replace the computer's copy of the file "menu.lst"?

---

### Post by sir.jeyhmis on 2009-09-30
(Thank you for correcting my "sudo fdisk-1" to "sudo fdisk-l)

---

### Post by oldfred on 2009-09-30
We need fdisk -l to see your drive and partition info to know how to correct you menu.lst. Also the blkid -L command will list your UUID's.
You could also post your menu.lst. Did you make a backup copy before you edited it?

From the live CD you can do all the corrections. I am not sure if from the live Cd you need the sudo command as I think it is by default?

Make backup then edit
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

---

### Post by nikhilk on 2009-10-01
> **sir.jeyhmis said:**
> Ok, so in the LiveCD terminal, I can use the command "sudo fdisk-l" to find the partitions and file types on my hard drive.
What does this information help me with?  Do I need the "sudo fdisk-l" info to find the menu.lst file?
This information is required to identify the Linux partition which contains the /boot directory and its contents. Using this information that particular partition can be mounted and screwed-up menu.lst file of yours can be repaired. Help me, help you.

Assuming that your Ubuntu boot partition is /dev/sda1 You would have to:
* Boot from live-CD
* Open a terminal and execute the following commands
```
mkdir /tmp/tmp_mount
```
```
sudo mount /dev/sda1 /tmp/tmp_mount
```
```
sudo cp /tmp/tmp_mount/boot/grub/menu.lst /tmp/tmp_mount/boot/grub/menu.lst.bak
```
```
sudo gedit /tmp/tmp_mount/boot/grub/menu.lst
```
Edit your menu.lst file and you should be all set.

---

### Post by sir.jeyhmis on 2009-10-01
I see.  Thank you!

This is what comes up after I use "sudo fdisk -l"

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        7304    58553344    7  HPFS/NTFS
/dev/sda3            7304        7441     1103560   83  Linux
/dev/sda4            7442       14593    57448440    5  Extended
/dev/sda5            7442       14295    55054723+  83  Linux
/dev/sda6           14296       14593     2393653+  82  Linux swap / Solaris

Does this mean that I should mount /dev/sda3 instead of /dev/sda1, which you did in your example?

---

### Post by sir.jeyhmis on 2009-10-01
> **oldfred said:**
> Did you make a backup copy before you edited it?

Yes, I did make a backup using the same command that you wrote.  The backup is exactly the same as the original from the CD because I didn't edit anything before backing up the menu.lst file.

---

### Post by sir.jeyhmis on 2009-10-02
> **nikhilk said:**
> This information is required to identify the Linux partition which contains the /boot directory and its contents. Using this information that particular partition can be mounted and screwed-up menu.lst file of yours can be repaired. Help me, help you.

Assuming that your Ubuntu boot partition is /dev/sda1 You would have to:
* Boot from live-CD
* Open a terminal and execute the following commands
```
mkdir /tmp/tmp_mount
``````
sudo mount /dev/sda1 /tmp/tmp_mount
``````
sudo cp /tmp/tmp_mount/boot/grub/menu.lst /tmp/tmp_mount/boot/grub/menu.lst.bak
``````
sudo gedit /tmp/tmp_mount/boot/grub/menu.lst
```Edit your menu.lst file and you should be all set.

Hey, thank you nikhilk for the help.  I followed your instructions, using sda5 and Grub is up and running.

Many thanks!

And thank you everyone else for your help as well, it is much appreciated!

---

### Post by sir.jeyhmis on 2009-10-02
(Is there a way to categorize this thread as "resolved?"  Is that something I should do, or will it automatically happen over time?  Thanks!)

---

