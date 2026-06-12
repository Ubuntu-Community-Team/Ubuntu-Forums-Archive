---
title: "Lost 8 years worth of pictures, please help!"
date: 2011-12-17
forum: General Help
---

### Post by YeeP on 2011-12-17
I have ubuntu 11.10 with an external hard drive for backup purposes. Originally I was just transferring folders to it, but recently tried the backup program. Apparently this program deletes what is there?? Either way, I know it is my fault.  I have been trying to use foremost to retrieve, but I possibly am doing something wrong.

Gparted has the external hard drive as /dev/sdb, but the partition is /dev/sdb1.  I have tried the following command with both and had no luck with file retrieval.

```
sudo foremost -t jpg -i /dev/sdb -o /foremost

```

and

```
sudo foremost -t jpg -i /dev/sdb1 -o /ryan/jpegs
```

all I have gotten is a buch of periods like this:
```
ryan@YeeP:~$ sudo foremost -t jpg -i /dev/sdb1 -o /ryan/jpegs
Processing: /dev/sdb1
|******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************|

```

Could anyone please help me? I have lost pictures from when my kids were born (not the actual birth!), kids first days at school, all that. PLEASE help!

---

### Post by Jerry N on 2011-12-17
I can't help get your pictures back but the question arises again:  Why does everyone have to lose something really important to them before they understand the concept of backups?  My many gigabytes of pictures, some dating back to the 50s, are on 3 hard drives at home and on a hard drive in my safety deposit box at the bank.  My motto concerning backups has for years been "Paranoia is a virtue"!

Jerry

---

### Post by docbop on 2011-12-17
I would say stop mucking around, the more you do things that might write to the drive the more data/photos you are killing off.    If you seriously wants these photos back go to someone with forensic tools that can recover data from even erased drives.   Be warned it will be EXPENSIVE.   

Then when done start putting together a real backup system.

---

### Post by philinux on 2011-12-17
> **YeeP said:**
> I have ubuntu 11.10 with an external hard drive for backup purposes. Originally I was just transferring folders to it, but recently tried the backup program. Apparently this program deletes what is there?? Either way, I know it is my fault.  I have been trying to use foremost to retrieve, but I possibly am doing something wrong.

Gparted has the external hard drive as /dev/sdb, but the partition is /dev/sdb1.  I have tried the following command with both and had no luck with file retrieval.


Could anyone please help me? I have lost pictures from when my kids were born (not the actual birth!), kids first days at school, all that. PLEASE help!

I accidentally deleted a few gig of mp3 files last. I recovered nearly all then used a batch renaming app to recover there original filenames.. I used photorec from testdisk to retrieve them. Do not write to the disk in question. Read up on this first. You need to specify a partition other than the external drive as a target destination for any recovered files. So it needs to be big enough. This could be your home directory for instance.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

On your main machine :-
```
sudo apt-get install test-disk
```
photorec is part of this program.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by pretty_whistle on 2011-12-17
Good advice philinux.

---

### Post by YeeP on 2011-12-17
> **Jerry N said:**
> I can't help get your pictures back but the question arises again:  Why does everyone have to lose something really important to them before they understand the concept of backups?  My many gigabytes of pictures, some dating back to the 50s, are on 3 hard drives at home and on a hard drive in my safety deposit box at the bank.  My motto concerning backups has for years been "Paranoia is a virtue"!

Jerry

Oh, I understand the concept. There are many ways to back up data. One of which can be where the data is literally copied and the backup drive does nothing other than hold copies. Leaving the user with the ability to not have to carry all of the backed up data on their main hard drive.  Which is exactly what I was doing. All of my family pics were on the backup drive, none of them on the machine hard drive.  The backup tool is apparently setup to mimic exactly what is on the drive.


philinux: I am looking into this tool right now. Thank you for the tip. :(

---

### Post by xyzzyman on 2011-12-17
> **Jerry N said:**
> I can't help get your pictures back but the question arises again:  Why does everyone have to lose something really important to them before they understand the concept of backups?  My many gigabytes of pictures, some dating back to the 50s, are on 3 hard drives at home and on a hard drive in my safety deposit box at the bank.  My motto concerning backups has for years been "Paranoia is a virtue"!

Jerry

So one EMP blast from a nuke in the atmosphere and there goes all your magnetic data. :) I have hard drive backup along with two sets of dvd's for my backups. The DVD's are different brand/dye's also.

---

### Post by 73ckn797 on 2011-12-17
> **philinux said:**
> I accidentally deleted a few gig of mp3 files last. I recovered nearly all then used a batch renaming app to recover there original filenames.. I used photorec from testdisk to retrieve them. Do not write to the disk in question. Read up on this first. You need to specify a partition other than the external drive as a target destination for any recovered files. So it needs to be big enough. This could be your home directory for instance.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

On your main machine :-
```
sudo apt-get install test-disk
```photorec is part of this program.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
This works.

---

### Post by bluexrider on 2011-12-17
YeeP, you might try testdisk and photorec. Worked when I needed it

> **Jerry N said:**
> I can't help get your pictures back but the question arises again:  Why does everyone have to lose something really important to them before they understand the concept of backups?  My many gigabytes of pictures, some dating back to the 50s, are on 3 hard drives at home and on a hard drive in my safety deposit box at the bank.  My motto concerning backups has for years been "Paranoia is a virtue"!

Jerry

Really, was there a need to grind on the OP. Sure lessons are hard sometimes but gezz.

Asking for help shouldn't be condescending.

---

### Post by 73ckn797 on 2011-12-17
> **bluexrider said:**
> yeep, you might try testdisk and photorec. Worked when i needed it



really, was there a need to grind on the op. Sure lessons are hard sometimes but gezz.

Asking for help shouldn't be condescending.
+1

---

### Post by Jerry N on 2011-12-17
> **YeeP said:**
> Oh, I understand the concept. There are many ways to back up data. One of which can be where the data is literally copied and the backup drive does nothing other than hold copies. Leaving the user with the ability to not have to carry all of the backed up data on their main hard drive.  Which is exactly what I was doing. All of my family pics were on the backup drive, none of them on the machine hard drive.  The backup tool is apparently setup to mimic exactly what is on the drive.


philinux: I am looking into this tool right now. Thank you for the tip. :(

But if you have only one copy of the data you don't have a backup, no matter what you call the drive that contains that data!

---

### Post by Jerry N on 2011-12-17
> **xyzzyman said:**
> So one EMP blast from a nuke in the atmosphere and there goes all your magnetic data. :) I have hard drive backup along with two sets of dvd's for my backups. The DVD's are different brand/dye's also.

After that blast, it probably won't make a lot of difference to me whether I have a backup or not:(

---

### Post by Jerry N on 2011-12-17
> **bluexrider said:**
> Really, was there a need to grind on the OP. Sure lessons are hard sometimes but gezz.

Asking for help shouldn't be condescending.

Condescension?  No it is more like lack of sympathy for people who lose their data and don't have backups.  I shall continue beating this drum.

Jerry

---

### Post by worksofcraft on 2011-12-18
I sympathise with you and have also lost more precious photos and data due to ill-conceived automated software tools than any other kind of malfunction, or environmental disaster.

It's not your fault at all. :(

---

### Post by lsemmens on 2011-12-18
Just as a thought, what format was the HDD on which the data was stored? I am still fairly new to the Linux realm so the tools for Linux are not familiar, however there are many good, and some, free, tools for recovering FATxx or NTFS file systems out there, but they run under M$ OS. Most of my other suggestions re: backup and not writing to the drive in question have already been covered. Just as a (rather obvious) thought, are they not all sitting in the trash?

---

### Post by philinux on 2011-12-18
> **lsemmens said:**
>  Just as a (rather obvious) thought, are they not all sitting in the trash?

I had assumed the OP had already explored that but if not then check there first for sure. Would be much simpler that photorec.

---

