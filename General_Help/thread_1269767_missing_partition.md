---
title: "missing partition"
date: 2009-09-18
forum: General Help
---

### Post by aiman15 on 2009-09-18
I realise after i installed Ubuntu Jaunty Jackalope... (Dual Boot with Windows XP MCE 2005)

i cant find my D partition...

In windows they manage to detect my D partition but not my ubuntu...

surprisingly ubuntu manage to detect my C and SWAP (windows) partition..

i tried sudo -ldisk and they manage to detect my D partition

so help me.. how to detect my D partition?? also to make my ubuntu use my D partition..

---

### Post by aiman15 on 2009-09-19
Bump

---

### Post by undecim on 2009-09-19
Let me make sure I under stand your question: You have C: partition, a D: partition, and and an Ubuntu partition (and a swap partition) on one drive. Windows can read C: and D:, but not Ubuntu, and Ubuntu can read C:, but not D:?

If you could include a copy of the output of "sudo fdisk -l", then that would be helpful.

---

### Post by Bucky Ball on 2009-09-19
Open Partition Editor (System->Admin). Can you see it there? The is a drop down list to the top right which should contain all the drives in the box.

What format is the partition?

You can also open a terminal (Applications->Accessories) and copy/paste this in:

```
sudo blkid
```It should show in the output. Post the output of that command back here.

[QUOTE=undecim]If you could include a copy of the output of "sudo fdisk -l", then that would be helpful.[/QUOTE]

Sorry, yea, either command will give us an idea. :)

---

### Post by aiman15 on 2009-09-19
thanx, i never had this problem with Hardy Heron...

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        3766     9767520    b  W95 FAT32
/dev/sda3            3767        4374     4883760   82  Linux swap / Solaris
/dev/sda4            4375        9729    43014037+   5  Extended
/dev/sda5            4375        5590     9767488+  83  Linux
/dev/sda6            5591        9729    33246486    b  W95 FAT32
```

for the data here.. i cant access **sda6**.. is there is any other way???

i want access there to read and remove files.. not reformating it

---

### Post by Bucky Ball on 2009-09-19
Firstly, try this:

```
sudo mount /dev/sda6
```If that mounts, unmount it again:

```
sudo umount /dev/sda6
```go to the appropriate directory, in this case:

```
cd /media
```and create a mount point directory for it:

```
sudo mkdir /media/your_mountpoint_name
```Then to /etc/fstab

```
sudo nano /etc/fstab
```Note: to avoid mishaps it is best to make a backup before changing with:

```
sudo cp /etc/fstab /etc/fstab.backup
```You can get some clues from here but looks a little dated:

[http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32](http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32)

... but I will be on my laptop shortly which has a fat32 partition mounted at boot and I figure out how I did it and get back to you with more exact instruction.

What version are you using? UUID I think is now used rather than /dev/sd*. You can find that with:

```
sudo blkid
```you would then have something like:

```
# /dev/sda6 (this line only identifier)
UUID (the appropriate number for sda6 goes here)   /media/your_mountpoint  **vfat iocharset=utf8,umask=000 0 0**
```I will get back to you with exactly what the part in bold needs to be shortly. (if someone else doesn't)

---

