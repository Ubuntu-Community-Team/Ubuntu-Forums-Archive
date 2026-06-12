---
title: "using gparted trying to resize partion"
date: 2010-04-16
forum: General Help
---

### Post by Bkc68 on 2010-04-16
trying to resize my partion using the gparted live cd., i want to shrink it so i can store stuff without losing it but i get a orange/yellow triangle with an exclamation point beside my partion im trying to shrink that has my main install on it(ubuntu 9.10) i have over 400gigs unused and it wont let me resize it..the detail error just says what my operation was..rezize the partion no real details at all

---

### Post by bwhite82 on 2010-04-16
Sorry, but I have to be thorough here, did you hit the 'apply changes' button?

---

### Post by Bkc68 on 2010-04-16
yes thats when i goes to to do it and then just stops and says it cant do it but in the details all  it says is the task that i was aplying

---

### Post by Bkc68 on 2010-04-16
i cant find what the exclamation point means..its there as soon as gparted starts

---

### Post by susanw on 2010-04-16
Hello,

Just checked GParted. I just get a yellow triangle by unallocated space - properties gives information on this marker as either - file system is damaged, unknown to GParted or no file system available (unformatted.) Not sure this helps?

Hopefully anything you are trying to change is unmounted. Also check the swap is off as this seems to be necessary too for some partition changes.

---

### Post by Bkc68 on 2010-04-16
ok  i found what it means but i dont know what it means..know what i mean?  lol....anyway  file system has unsupported features while trying to open dev/sda1 couldnt find file system superblock

---

### Post by wilee-nilee on 2010-04-16
Are you doing this from a live CD and do you have swap turned off, if not you should be. Everything if in order can be moved if there is room, but there is always the chance of losing everything, so have a backup of what you would need in case of this scenario.

You also might tell us the OS of the partition your trying to adjust.

You might post the output of this terminal command 
sudo fdisk -l   

l=lower case L

---

### Post by Bkc68 on 2010-04-16
maybe this will help also 

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 3145796 has zero dtime.  Fix? no

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (106608228, counted=106719296).
Fix? no

Inode bitmap differences:  -3145796
Fix? no

Free inodes count wrong (29777149, counted=29777478).
Fix? no


/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 189187/29966336 files (0.3% non-contiguous), 13226623/119834851 blocks

---

### Post by Bkc68 on 2010-04-16
yes im using a live cd

---

### Post by wilee-nilee on 2010-04-16
> **Bkc68 said:**
> yes im using a live cd

It is hard to tell if any damage has been done. Also have you turned off swap gparted will not resize the partition without doing so.

---

### Post by Bkc68 on 2010-04-16
wilee i looked to turn it off while in the the live cd but the unmount feature was greyed out only thing on the partion is ubuntu 9.10

---

### Post by wilee-nilee on 2010-04-16
> **Bkc68 said:**
> wilee i looked to turn it off while in the the live cd but the unmount feature was greyed out only thing on the partition is Ubuntu 9.10

I am a little confused, you should see swap off not unmount when you right click on the swap partition. This might be what you mean it is hard to tell.

Thats about the best of my knowledge, hope you get it worked out.

---

