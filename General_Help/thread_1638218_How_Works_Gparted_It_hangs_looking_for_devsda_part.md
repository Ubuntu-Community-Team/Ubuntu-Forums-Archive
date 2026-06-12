---
title: "How Works Gparted? It hangs looking for /dev/sda partitions."
date: 2010-12-05
forum: General Help
---

### Post by pgibson on 2010-12-05
Last weekend I deleted an unused logical volume (/dev/sda7 ... ext3)to make some space, and immediately thereafter Gparted couldn't find the partitions on /dev/sda.  I was using the Ubuntu 10.04 live CD, but I tried various other sources of Gparted with no success.

Here's my current output from fdisk -l, if that's any help

```
[COLOR="Green"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb2a2b2a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        6374    30716280   83  Linux
/dev/sda4           10199       19457    74372917+   f  W95 Ext'd (LBA)
/dev/sda5           10199       10517     2562336   82  Linux swap / Solaris
/dev/sda6           10518       14341    30716248+   c  W95 FAT32 (LBA)
[/COLOR]
```

Googling the problem suggested problems with the MBR/grub ... and many many hours of testdisk and grub and like that has taken me a long way, but I'm not there yet.

I can currently boot everything fine, and after upgrading to 9.10, [purging/reinstalling grub2]("http://ubuntuforums.org/showthread.php?t=1581099") I *can* mount from live CDs (which I couldn't do immediately after gparted stopped working).

I'm wondering, then, if how Gparted "looks" at the drive, that maybe it's a case of information being where it shouldn't be, or some such.  Any new information or insight would be deeply appreciated.

---

### Post by lindsay7 on 2010-12-05
Looks like you have some unallocated space where sda7 was.  If so you can grow an other partition into it or make a  new partition.  I can not be sure without looking at the sda drive.  Can you post a screen shot of the drive showing what gparted displays for the drive info?

---

### Post by lindsay7 on 2010-12-05
this is what I am looking for, example

[ATTACH]177493[/ATTACH]

---

### Post by pgibson on 2010-12-05
Sure thing, here's gparted not finding the /dev/sda partitions and disk utility showing the various spaces on the same drive.

---

### Post by ronparent on 2010-12-05
Can you get anything if you call gparted in a terminal as such - sudo gparted /dev/sda

---

### Post by lindsay7 on 2010-12-05
found this,

Kyle,

Try :

1. Boot into the liveCD and go live session (try ubuntu ...). Access a terminal and type

Code:

sudo apt-get remove dmraid

Close terminal and proceed to install.

2. Another tip provided by presence1960 is to make sure in step 4 of the install process that the proper HD is selected in the upper right Box.



this is the thread.  [http://ubuntuforums.org/showthread.php?t=1349898](http://ubuntuforums.org/showthread.php?t=1349898)

---

### Post by pgibson on 2010-12-05
Ronparent: 
[INDENT]Thanks for the tip.  I tried that early on but to no avail.  I haven't re-tried it. Lemme see what happens.[/INDENT]

Lindsay:
[INDENT]This sounds promising, from what I can understand about dmraid and what it seems to do (and without a thoroughgoing course on the subject).;)

I've looked at the thread you pointed to, and I'm not clear on what they were doing ... at some points it sounds like "install" is talking about connecting a hard drive, and at other times, perhaps installing an OS.

What will it do to remove dmraid?  It certainly is in the right area (LVM and like that).  I'm hoping to understand this better.:)[/INDENT]

---

### Post by pgibson on 2010-12-06
Lindsay, thanks for the pointer towards dmraid.  Though I couldn't find anything on my hard drive saying "raid," nor indeed, improve things with sudo apt-get remove dmraid, your posts and links got me thinking in the right direction to formulate a plan of action.  Following links you gave me I ended up reading a lot here:

[[COLOR="Blue"]http://gparted-forum.surf4.info/viewtopic.php?id=576[/COLOR]]("http://gparted-forum.surf4.info/viewtopic.php?id=576")

Though I'll not know exactly what was going on, Gparted has had a problem with logical partitions and dmraid, so I came up with an end run around the whole issue:

I used Disk Utility to create a Primary FAT partition on 31G of unallocated space and copied into it all the contents of /dev/sda6.  I then used Disk Utility to delete /dev/sda4.  I had read swap wasn't strictly necessary anymore, and though /etc/fstab complained about its absence, Ubuntu started fine. 

 There was a sort of "ghost" of /sda6 that remained listed and I deleted the copy thinking I had not lost the partition ... oops!  Can't mount or see the ghost partition.  :D  Gone.  HA! Well, I had backed everything up elsewhere before this whole odyssey began, so I can get it back. I may try recovering it with test disk just to see if I can.

In the end, I got what I wanted: Gparted can once again see my partitions, both primary, on my hard drive.

Ignorant gui noob has drive back.

Yay.

Peace.

---

