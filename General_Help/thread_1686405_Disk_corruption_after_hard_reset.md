---
title: "Disk corruption after hard reset"
date: 2011-02-12
forum: General Help
---

### Post by Jimmy9pints on 2011-02-12
Hello,

I'm facing a big problem with a corrupted disk on my wife's computer after she hard resetted the box after it froze up solid. 

Upon restarting it dropped into Busybox reporting something like
> No init found. Try passing init= boot arg BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash) (initramfs) ...

This is VERY similar to a problem I had just a few weeks back with my own computer - see [this thread]("http://ubuntuforums.org/showthread.php?t=1666719") for details of that. 

From that problem I learnt a lot, so I thought this would be quite straight forward, but I've ran into problems. 

The first thing I did was get a live disk, I chose Ubuntu Rescue Remix. It's a command line interface, which I am ok with, but I can't copy/paste the outputs here....so I am currently downloading System Rescue CD. 

sda1 is the root partition, it is corrupted. I used dd to make a back up of that by mounting sda7, and dding the whole partition image into /mnt/sda7/sda1.img . 

This seemed to complete properly, but, when I ran e2fsck on that img file, it wouldn't complete, throwing up a lot of errors. 

```
ubuntu@ubuntu:/mnt/sda7temp$ sudo e2fsck sda1.img e2fsck 1.41.12 (17-May-2010)
Error reading block 2129920 (Invalid argument).  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 2129920 (Invalid argument).  Ignore error<y>? yes

Superblock has an invalid journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Superblock has_journal flag is clear, but a journal inode is present.
Clear<y>? yes

The filesystem size (according to the superblock) is 4292352 blocks
The physical size of the device is 1048575 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

Error writing block 2129920 (Invalid argument).  Ignore error<y>? yes
```

Of course, after that, mounting the image file using "mount -o loop" as I used last time didn't work. 

```
mount: wrong fs type, bad option, bad superblock on /dev/loop2,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so
```

fdisk -l gives some output about "Partition x does not end on cylinder boundary." for all the partitions. 

When I download and boot into System Rescue CD, I'll be able to run some more tests, in the mean time, if you have any ideas or questions, please fire away!!! 

I really want to save this disk otherwise my wife will be back on Windows permanently. :(

Thanks people!

Jimmy

---

### Post by amsterdamharu on 2011-02-12
> a superblock, containing a [magic number]("http://en.wikipedia.org/wiki/Magic_number_%28programming%29")  identifying this as a UFS filesystem, and some other vital numbers  describing this filesystem's geometry and statistics and behavioral  tuning parametersI've had some trouble with mbr being messed up (suspect Windows) and have an unbootable (not even grub) machine. For this reason I created a tinycore usb bootable and backed up the first 512 bites of the disk and every partition.

Here is the script to do so:
```
for hds in $(fdisk -l | grep -i '^Disk /' | awk -F' ' '{print $2}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}')
    hds=$(echo $hds | awk -F':' '{print $1}')
    echo $hds
    dd if=/dev/$hds of=$hds.bin bs=512 count=1
done
for hds in $(fdisk -l | grep -i '^/dev/' | awk -F' ' '{print $1}');
do
    hds=$(echo $hds | awk -F'/' '{print $3}');
    dd if=/dev/$hds of=$hds.bin bs=512 count=1
done
```Normally I put a copy of that back and see if it works first, since this is the second incident maybe you should be thinking of backing up this stuff as well.

Good news is that superblock is backed up somewhere and can be restored:
[http://www.linfo.org/superblock.html](http://www.linfo.org/superblock.html)
To check where the superblock is backed up (usually 8193, 24577, 40961, 57345 and 73729) use the following command:
```
sudo dumpe2fs device_name | grep super
```Then use e2fsck to check the device:
```
sudo e2fsck -f -b block_offset device
```The block_offset is one of the numbers you got from the dumpe2fs command.

Have to say I never did this and not sure how current these articles are but you still have the original device and only execute the commands on the copy you made with dd so it should be fine.

---

### Post by amsterdamharu on 2011-02-13
I just had a thought, if the superblock has info about the geometry (size?) of the partition and the superblock is corrupt then how does dd make a good copy of the partition?

In other words, can dd make a copy of the partition if the superblock is damaged?

---

### Post by Jimmy9pints on 2011-02-13
Thanks for your reply!

> since this is the second incident maybe you should be thinking of backing up this stuff as well.

This is the second incident of this kind, but it's a different machine! Both are Asus eeepc (1005HA and 1001PQ), both run Ubuntu (Maverick, Lucid respectively). I started backing up my machine (at least my documents) using Ubuntu One, but couldn't get access to my wife's computer for long enough to sort that out for her! Ooops!


> 
In other words, can dd make a copy of the partition if the superblock is damaged? 

I have no idea. After doing a lot of reading around, testdisk and ddrescue sound promising. I am now making a "rescued" image of the disk using ddrescue. 

Once I have that img. I'll make a copy of it and run dumpe2fs and e2fsck on it as you suggest. I'll also try testdisk....

Will let you know how it goes. 

Jimmy.

---

### Post by Jimmy9pints on 2011-02-13
OK, things are not going well.

I set ddrescue off on its mission and all was going well for quite some time. It was flying along at a rapid rate reporting no errors at all for about the first 10 minutes...then all of a sudden, it ran into errors and has been crawling along since. 

Attached is a picture of the kind of thing that's been scrolling down my screen for the last 3 hours....

I really hope I am going down the right route here and not further damaging things!!

:confused:

Do errors on ddrescue indicate hardware damage???

---

### Post by Jimmy9pints on 2011-02-13
It looks like I have a hardware failure on my hands. Plenty of I/O errors scrolling down my screen right now. 

Here are some useful links for people suffering the same problem. 

_People who had similar problems_
[https://help.ubuntu.com/community/DataRecovery#Guidelines](https://help.ubuntu.com/community/DataRecovery#Guidelines)
[http://blog.octo.com/en/how-to-rescue-your-data/](http://blog.octo.com/en/how-to-rescue-your-data/)
[http://blog.octo.com/en/how-to-rescue-your-data-23/](http://blog.octo.com/en/how-to-rescue-your-data-23/)
[http://blog.octo.com/en/how-to-rescue-your-data-33/](http://blog.octo.com/en/how-to-rescue-your-data-33/)
[http://ubuntuforums.org/showthread.php?t=1206225](http://ubuntuforums.org/showthread.php?t=1206225)
[http://www.linuxquestions.org/questions/linux-hardware-18/corrupted-drive-mechanical-or-logical-fsck-repair-830854/](http://www.linuxquestions.org/questions/linux-hardware-18/corrupted-drive-mechanical-or-logical-fsck-repair-830854/)
[https://bbs.archlinux.org/viewtopic.php?pid=571586](https://bbs.archlinux.org/viewtopic.php?pid=571586)
[U]
Software[/U]
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)
[http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)

---

### Post by Insuite on 2011-02-23
HIya Jimmy...

I am having the a very similar problem.  I have 10.10 on one partition and Win 7 on another.  I too have a ASUS MOBO but socket 775 version.  I have very recently reinstalled Ubuntu and the same problem started again.  The system freezes, hard reset and then I get on reboot either...
grub error
disk not found
or
the HD disk name corrupted to complete rubish in the bios.
a hard reset again garners the same results, however if I turn the machine off, the corrupted HD name is gone and the correct is back and the system boots.

Here is an interesting link where the guy is having the same or very similar problem and it turned out to be a RAM module,,,
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-server-random-hard-drive-corruption-792174/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-server-random-hard-drive-corruption-792174/)

I didn't mention that I switched from a Biostar mobo as I had read that their SATA chips had a tendency to corrupt HD's.  I was having the same problem there as well.

I have noticed that if I unplug my SATA DVD drive from the mobo it sometimes fixes the problem temporarily.  It is all very strange!!!!

I like your posts but unfortunately, i do not speak linux near as fluent as you do.

Cheers,
Insuite

---

### Post by TxRx on 2011-06-21
Jimmy, thanks for posting both of your threads here, it's been a big help for myself since I've had it twice in the same unit with the same drive. 

Mine is looking very much like drive failure, your hard work has helped save me so much time and I thoroughly appreciate it and the replies from others on this very topic.

---

### Post by Jimmy9pints on 2011-06-21
Very glad that it helped.

---

