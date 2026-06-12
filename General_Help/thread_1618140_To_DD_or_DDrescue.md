---
title: "To DD or DDrescue?"
date: 2010-11-10
forum: General Help
---

### Post by Bow-Man on 2010-11-10
Ok, I have spent the last day trying to figure this out. Google is great when you have a general knowledge of what you are trying to accomplish. Sadly most help I found assumes more expertise in Linux that I currently have.

My situation. I have a 250G drive that is in its death-throws. I have a 2 TB drive that I use as a data storage/backup drive.

I want to recover the 250G drive to a "folder" on the 2 TB drive. I do not want to lose any data on the 2 TB drive.

Since the source drive is on its last legs.. I want it to just copy over. I know there are going to be errors, so I don't want to have to acknowledge every one.

I know which drive is which in drive manager, or /media/ if its mounted.

Once I am done this, I intend on using sleuthkit or something similar to try and recover what I can. I tried to use testdisk to create an image, and let it run over night, but in the morning, I had a 2G image file (there is at least 100G of data on the drive), so I know it did not work right.

I am using a USB drive caddy to hold the drives that beeps every 8 seconds. After 14 hours of that, I am starting fresh... minus a piezoelectric speaker on the circuit board which lost a fight with a soldering iron. :) 

So, if anyone could help me out, it would be greatly appreciated.

---

### Post by Bow-Man on 2010-11-12
48 hour bump.
No one has any advice?

---

### Post by tomdkat on 2010-11-12
I'm in a similar boat.  :)

What filesystem is on the drive you want to backup? The 250GB drive?

Today, I found [this thread](http://ubuntuforums.org/showthread.php?t=1615643&highlight=ddrescue) which mentions ddrescue and ntfsclone.  In my case, I'm wanting to get data off a dying 250GB drive formatted with NTFS.

Peace...

---

### Post by alphaamanitin on 2010-11-12
If you have I/O errors dd or ddrescue is supposed to be dangerous.  At least I am 99% confident that I read that while researching dd and ddrescue.  I think dd might be could for you, particularly if you used the no error or no truncate stuff.  ddrescue tries to fill in the damaged sectors if I remember correctly.  Also, barring I/O erros I think you should be able to do either see how it works and try the other one without issues.  

AlphaA

---

### Post by Bow-Man on 2010-11-12
> **tomdkat said:**
> I'm in a similar boat.  :)

What filesystem is on the drive you want to backup? The 250GB drive?

Today, I found [this thread]("http://ubuntuforums.org/showthread.php?t=1615643&highlight=ddrescue") which mentions ddrescue and ntfsclone.  In my case, I'm wanting to get data off a dying 250GB drive formatted with NTFS.

Peace...


Both the 250G and 2 TB drive are NTFS. Since I am primarily fixing Windows issues, and Windows cannot write to a Linux file system. The 250G is a drive out of a live system, the 2TB drive is used only as a backup, and is not bootable.

I will take a look at the ntfsclone tool.

Thank you for your reply.

---

### Post by cbraxton on 2010-11-12
What I usually do in that kind of situation is to use dd_rescue to make an image copy of the entire drive, then work with that for data recovery. For example, if the failing drive comes up as /dev/sdb, you would enter something like:

```

dd_rescue -b 2096K -A /dev/sdb sdb-image.img

```

The "-b" option sets a larger block size to speed up copying when there are no errors. (Though dd_rescue does not like very large block sizes, it will abort on an error if you specify too large a value.) 

The "-A" option always writes to the output file, zeroes in the case of read errors. (This gives you a shot at keeping the layout of the filesystem intact.)

Once you have the image you can mount it using loopback, or copy to another drive for analysis and possible data recovery.

I've recovered data from a number of failing drives this way, including a RAID0 fakeraid array when one of the drives was going bad and the array could not otherwise be assembled.

---

### Post by Bow-Man on 2010-11-12
> **cbraxton said:**
> What I usually do in that kind of situation is to use dd_rescue to make an image copy of the entire drive, then work with that for data recovery. For example, if the failing drive comes up as /dev/sdb, you would enter something like:

```

dd_rescue -b 2096K -A /dev/sdb sdb-image.img

```The "-b" option sets a larger block size to speed up copying when there are no errors. (Though dd_rescue does not like very large block sizes, it will abort on an error if you specify too large a value.) 

The "-A" option always writes to the output file, zeroes in the case of read errors. (This gives you a shot at keeping the layout of the filesystem intact.)

Once you have the image you can mount it using loopback, or copy to another drive for analysis and possible data recovery.

I've recovered data from a number of failing drives this way, including a RAID0 fakeraid array when one of the drives was going bad and the array could not otherwise be assembled.



Will this allow me to put the image on a different drive without damaging the existing data on that drive? If so, then this will do perfectly.

---

### Post by SecretCode on 2010-11-12
I've used ddrescue with great success, recovering an ext3 and an ntfs partition off a dying drive. I don't know any way it could damage the data - as long as you are writing to a different physical drive. (Don't write any more data to anywhere on the failing drive, with any software at all!)

Depending on how serious the errors are it can take a while. But using the log feature of ddrescue, you can run successive passes & retries to get more of the data off.

When you can't usefully get any more off, make a copy of the image (another 250GB) and perform file system recovery on that.

The images/copies on your 2TB drive will be just files. ddrescue doesn't perform any low-level reads or writes on the image drive. I haven't heard of any problem like that.

---

### Post by dcstar on 2010-11-12
> **SecretCode said:**
> I've used ddrescue with great success, recovering an ext3 and an ntfs partition off a dying drive. **I don't know any way it could damage the data** - as long as you are writing to a different physical drive.
............

Exactly, why people come to these insane conclusions is bizarre (at least).

The only "danger" of using ddrescue is that it can't access some data on irrecoverable disk blocks and anyone not paying attention to the reporting may believe that all of their data has actually been copied. That is not a problem with ddrescue, that is a problem with the person using it.

---

### Post by cbraxton on 2010-11-13
> **Bow-Man said:**
> Will this allow me to put the image on a different drive without damaging the existing data on that drive? If so, then this will do perfectly.

Yes, absolutely, as long as you are writing to a different drive you will not affect the original data. (Unless the source drive completely craters on you during the attempt, but you need to take that chance to extract the data in the first place.) Obviously you need to be sure the target drive is of sufficient capacity and the transfer will take a while, especially when the bad sectors are hit as dd_rescue drops the transfer rate down to a single 512-byte block at a time (by default) to get as many readable sectors as possible.

Also in my example I meant to use "-b 2048k" for a 2-Megabyte block transfers. I usually try to make that value as close as possible to the size of the drive's onboard buffer, but if you make it too large dd_rescue will complain and exit.

---

### Post by indytim on 2010-11-13
As an alternative to the dd approach, you may want to take look at Fsarchiver as it's bundled to SysRescueCD (a live CD).  Basically, fsarchiver will make a backup image file composed of all of the files / folders in your origination partition.  The app works well with all conventional file systems.  One of the big advantages in your situation is that the app computes a md5 checksum on all files and folders written to the backup.  In theory, at least, this should provide a visibility to any corrupted files as result of your hard drive situation.

One cautionary note, if your hard drive is dying, you may find it advisable to exercise it as little as possible until you execute the backup (whatever solution you choose to run).

Links:

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Footnote : I'm running Fsarchiver as my principal weekly backup app covering a 17 partition lineup.  I have successfully recovered ext3, ext4 and ntfs filesystem partitions using fsarchiver.

IndyTim / DataMan

---

### Post by Bow-Man on 2010-11-19
sudo dd_rescue -b 2096K -A /dev/sdg /dev/sdf my-image.img

This is the command that I am using, and it is not working. What am I doing wrong? (note: both drives are un-mounted)

I am running Ubuntu on this desktop, both my live windows drive, and backup drive are connected via usb. I do not want to copy any data to my Ubuntu HDD. 

I want to copy it from one external HDD to another external HDD the source is 250G the destination is 2TB.

Thanks for all the help so far.

---

### Post by Bow-Man on 2010-11-19
sudo dd_rescue -b 2096K -A /dev/sdg /dev/sdf my-image.img

Got it... changed it to;

 sudo dd_rescue -b 2096K -A /dev/sdg /media/backupdrive my-image.img
Had to mount the backup drive, but it looks like it is going now.

---

### Post by s8472 on 2011-02-14
Hi everyone,
I am trying to take an image of my ext4 root partition of my Ubuntu AMD64 install.  I use SystemRescueCD 2.0.0 to boot up.  When I do this:

```
mkdir /mnt/ydk
mount /dev/sdb1 /mnt/ydk
ddrescue /dev/sda3 | bzip2 -z -9 > /mnt/ydk/root-img.bz2
```

all I get is:

```
ddrescue: both input file and output file must be specified. Try ddrescue --help
```

I have been through the info and man pages several times and yet cannot locate an answer to this problem.

Any light as to the reason of this error message, or any pointers in the right direction would be much appreciated.

Thanks in advance.

---

