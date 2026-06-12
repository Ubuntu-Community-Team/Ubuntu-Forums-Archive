---
title: "Malicious command on dual boot &quot;mkdosfs -F32 -n IPOD /dev/sda1&quot;"
date: 2010-01-31
forum: General Help
---

### Post by toddmmmmmm on 2010-01-31
Hi all, I was trying to configure my IPOD Shuffle to work without installing Itunes on my windows XP partition, and upon reading the GTKPOD.org FAQ on the subject, I found this command

mkdosfs -F32 -n IPOD /dev/sda1

I established SU root access and did it. Now windows will not boot, and all of 
my years worth of backups on this hard drive do not exist! I don't think the drive 
was formatted so quickly but I cannot boot into windows anymore!
If anyone can help me with this, you would be a life saver! My whole american
livelihood is stored on that partition just weeks before I would have purchased
a large enough drive to back it all up too!
Help!
Thank you so much for all of your thoughts!
-Todd M from Pennsylvania

---

### Post by Leppie on 2010-01-31
you could try to restore using testdisk (for me it worked): [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
if you still have access to your ubuntu install or have a livecd at hand, you can install it from the repos:
```
sudo apt-get install testdisk
sudo testdisk
```

---

### Post by mrtomservo on 2010-01-31
I'm no expert on data recovery, but you may be able to recover your data.  Make sure you DON'T WRITE ANYTHING ELSE TO THAT PARTITION. (sda1)  Don't touch it until someone else can suggest something to you. If you write to it, you data may be lost. I'm sorry to say it may already be lost. I hope not though, I really hope you can recover it.  I know this doesn't help now, but in the future make sure you know which partition you're writing to before formatting it.  You can do that by ```
sudo fdisk -l
``` and then checking for the size/partition type that seems right for the device you're trying to format.  IE if it's NTFS and a large size in GB then it's probably not your ipod.

PS - wrote this before I saw Leppie's advice, didn't mean to offend when I said "Don't touch it until someone else can suggest something to you". :)

---

### Post by t0p on 2010-01-31
Here's some more advice you don't particularly want: **Don't type in commands unless you know what they're supposed to do... especially as root!**

Let's take a look at the **mkdosfs** manpage:

> MKDOSFS(8 )

NAME
       mkdosfs - create an MS-DOS file system under Linux

SYNOPSIS
       mkdosfs  [ -A ] [ -b sector-of-backup ] [ -c ] [ -l filename ] [ -C ] [
       -f number-of-FATs ] [ -F FAT-size ] [ -h number-of-hidden-sectors  ]  [
       -i volume-id ] [ -I ] [ -m message-file ] [ -n volume-name ] [ -r root-
       dir-entries ] [ -R number-of-reserved-sectors ] [ -s  sectors-per-clus&#8208;
       ter ] [ -S logical-sector-size ] [ -v ] device [ block-count ]
Your command told Linux to create an MS-DOS filesystem called "IPOD", in Fat32 format, in partition /dev/sda1.  Was /dev/sda1 your Windows partition by any chance?

You say you think the partition couldn't have been reformatted in the time between issuing the command and realising something was up.  If so, the data is probably (mostly) retrievable.  You may just need to recreate your MBR.  Otherwise, look in Synaptic for data recovery programs.

---

