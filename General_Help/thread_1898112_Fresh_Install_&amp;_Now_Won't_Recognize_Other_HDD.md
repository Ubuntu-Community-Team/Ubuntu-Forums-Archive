---
title: "Fresh Install &amp; Now Won't Recognize Other HDD"
date: 2011-12-20
forum: General Help
---

### Post by dibbster on 2011-12-20
Hi guys, new here.  I'm not very experienced :confused: -- just played around with linux for a while now casually.  Anyway, I just installed Ubuntu on my msata ssd and did a clean wipe.  I use my spinning drive for storage and Ubuntu use to to recognize this automatically (was dual booting with windows).  But now it will not mount and in device info it doesn't even show type as NTFS.  In whatever command I used that I found somewhere in the terminal it didn't show it either.

Please help as all my backups are on that drive and now that I don't have windows I can't access it for anything. Most distros I've tried or used for a while automatically found and mounted it.  I'm not sure what happened -- only thing I can think is that during the initial install some things were put on the spinner and it messed it up somehow.  I say this because after I installed it would hang on a blank screen and I had to re-install again to get it to work.  Thanks!

dibbs

---

### Post by QIII on 2011-12-20
Quick check --

Run the Live CD and see if the HDD is recognized and that you can view/manipulate files.

If that doesn't work, the fun starts.

(Oh, I hate to say this, but I still do these things:  Check that the HDD is plugged in.  I hate spending hours diagnosing something and then kicking myself in the rear because something is unplugged.)

---

### Post by dibbster on 2011-12-20
Hi, nope the livecd doesn't recognize it either >_<  
It is plugged in (its in my laptop) and it does show up in the disk utility.  Format says unknown (0x42).
I've been looking all over for a solution but I think the install messed something up initially but I could be wrong of course.
Thanks for the reply.

---

### Post by QIII on 2011-12-20
Pop the live cd back in and go to the terminal.

```
sudo gparted
```

See if it shows two drives, ie:  sda and sdb.  Don't change anything.

Let us know what you see.

---

### Post by dibbster on 2011-12-20
under partition there it shows /dev/sda1 file system: unknown (this is my hard drive) it is flagged as a boot drive apparently

under that in partition it says unallocated 1mb - -

in the upper right i can click and select the sda1 or dev/sdb (my ssd with OS installed) or below that dev/sdc which i am assuming is the thumb drive.

thanks for your help thus far my friend!

---

### Post by QIII on 2011-12-20
Ok.   Get out of the live session.  I just wanted a "sterile" look. 

Reboot normally, go to the terminal and do

```
sudo fdisk -l
```

That's an "ell" not a "one".

Post the results.

---

### Post by dibbster on 2011-12-20
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf38f13e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625140399   312570168+  42  SFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   139763711    69880832   83  Linux
/dev/sdb2       139765758   156301311     8267777    5  Extended
/dev/sdb5       139765760   156301311     8267776   82  Linux swap / Solaris

---

### Post by QIII on 2011-12-20
On that 320 GiB disk, I'm assuming you had all of you pictures of uncle Bob's funeral, your old family dog Fluffy, your movie and music collections and a bunch of critical business documents?

---

### Post by dibbster on 2011-12-20
i don't like the sound of that question lol.  mostly movies music docs and some pics really.  i'd obviously prefer to recover it if possible but it wouldn't be the end of the world.  is it gone?  any idea what happened and if windows would still read it?  thanks.

---

### Post by QIII on 2011-12-20
I'm going to take a wild stab here and suggest that the sfs file system indicates "secure file system" and that disk may be encrypted.  Do you remember clicking anything that said "encrypt"?

We could get lucky and find that its Simple File System...

---

### Post by dibbster on 2011-12-20
weird, no.  i was dual booting windows and mint for a while and i installed ubuntu through wubi a few days ago. really liked it and decided to just wipe the drive and just do ubuntu on it (the sdd).  the other drive has always just been storage/backup.  never had it encrypted and i don't remember ever clicking on anything like that.

---

### Post by QIII on 2011-12-20
Let me study on this a bit.  In the meanwhile, download and burn a copy of TestDisk.  There is a great little utility called PhotoRec which can recover a wide variety of file types from a lot of cobbled up systems. 

Or, if we are lucky, someone will come along and say "Heck, this is easy!"

---

### Post by dibbster on 2011-12-20
Yes let's hope so!  i really appreciate the time you took to help me out thus far.  i'll keep looking around for a solution.

---

### Post by QIII on 2011-12-21
Unfortunately, the more I read the less hopeful I become.  SFS appears to be a secure file system in a Windows world.  Are you absolutely sure you didn't do any "securing" or "encrypting" from Windows?  Do you have a disk password set in the BIOS?

Don't do anything rash, like reformatting.  This may not be at all what it seems at the moment.

---

