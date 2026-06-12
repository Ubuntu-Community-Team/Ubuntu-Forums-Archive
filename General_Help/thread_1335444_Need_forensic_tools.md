---
title: "Need forensic tools"
date: 2009-11-23
forum: General Help
---

### Post by mavigozler on 2009-11-23
A friend has been accused of sending ONE INSTANCE of an email message that someone has alleged is sexual harassment.

The police seized his computer, took an image of several storage devices, and claim that on his hard disk they found the message. The police have not provided their evidence (yet), but the friend says that the police probably searched for 3 strings and got hits on them, and from this assumed that this is evidence of the message.  He has believes that the string searches were related to other legitimate activity on his computer (it's too detailed to present the defense here).

We have received the computer back from the police, which was incidentally held 18 days, and which is 18 days after the police promised to return it to this person (they promised to take the image within the same day and then return the computer, but as a rule, the police likely don't have to do anything they promise and never do).

We want to search the computer ourselves to see if the message is really there, but want to boot from my USB stick with Ubuntu 9.04.

But we need forensic software or tools, or at least something that can do sector-by-sector, head-by-head disk searching, not just search the filesystem, but also the free space and deleted space.  

Any suggestions regarding software?

---

### Post by madinc on 2009-11-23
what have you tried?

---

### Post by madinc on 2009-11-23
have you tried ?

tct

sleuthkit

rdd

foremost

unhide

scalpel

---

### Post by t0p on 2009-11-23
**Sleuthkit** and **autopsy** are 2 computer forensics packages that are available through apt-get/Synaptic.  From Synaptic:

> Together, The Sleuth Kit
and Autopsy provide many of the same features as commercial digital forensics
tools for the analysis of Windows and UNIX file systems (NTFS, FAT, FFS,
EXT2FS, and EXT3FS).

It seems that the police in some jurisdictions are using [SAFE]("http://www.policemag.com/Channel/Technology/News/2009/11/12/ForensicSoft-Releases-Updated-SAFE-Computer-Forensic-Software.aspx").  But this is likely to cost a pretty penny.

I don't think it would be a good idea to do this on a "do-it-yourself" basis.  Your friend needs to employ a computer forensics specialist to do any analysis that he wants to enter into evidence.  The court is not likely to have much time for an amateur job.

On a side note: when an associate of mine was arrested and his computers seized for forensic examination, the police actually retrieved and printed out documents that they were interested in - ie they did not just search for some strings.  Unless your friend actually knows that the file in question was never on his machine, I would suggest that the police have actually found it there.

Not to worry though: if the case goes to court, discovery rules mean that your friend will get a full statement of the "evidence" long before a trial date.

---

### Post by QLee on 2009-11-23
> **mavigozler said:**
> A friend has been accused of sending ONE INSTANCE of an email message that someone has alleged is sexual harassment.

The police seized his computer, took an image of several storage devices, and claim that on his hard disk they found the message. The police have not provided their evidence (yet), but the friend says that the police probably searched for 3 strings and got hits on them, and from this assumed that this is evidence of the message.  He has believes that the string searches were related to other legitimate activity on his computer (it's too detailed to present the defense here).

We have received the computer back from the police, which was incidentally held 18 days, and which is 18 days after the police promised to return it to this person (they promised to take the image within the same day and then return the computer, but as a rule, the police likely don't have to do anything they promise and never do).

We want to search the computer ourselves to see if the message is really there, but want to boot from my USB stick with Ubuntu 9.04.

But we need forensic software or tools, or at least something that can do sector-by-sector, head-by-head disk searching, not just search the filesystem, but also the free space and deleted space.  

Any suggestions regarding software?

If you want to use this in a legal defence you should consider employing the services of a specialist, preferably one who has experience as an expert witness and thus can convince a judge and/or a jury who won't understand computer forensics. And I suggest you have the police return the computer directly to your expert or else the chain-of-evidence is broken and anything you say isn't there could have been deleted by you.

Note:
I am not a lawyer.

--
Edit: I see that one other poster agrees, you should consider it.

---

### Post by mavigozler on 2009-11-26
Thanks for all the helpful advice.

I think the Autopsy web interface to the sleuthkit will probably do what I need to do.

The problem is, Autopsy/sleuthkit requires an image file to be created first, and it does not explain how it is to be done.  I actually want to create the image file now, since the disk is to be used for other work now, and cannot be until that image is made.

I have learned that programs like proprietary (and expensive) EnCase can be used, but so can the GNU utility 'dd', which apparently comes naturally installed with Ubuntu.

I want to put the image of the target on my 1 TB (0.91 TiB) drive.

I have installed KDE Partition Manager to get information on the devices which are the image target and the image itself.

The target is a 100 GB (93.16 GiB) physical drive (Seagate ATA ST910021AS).  KDE PartMan reports:

Path: /dev/sda
Type: msdos
Capacity: 93.16 GiB
Total Sectors:  195,366,465
Heads: 255
Cylinders: 12,161
Sectors: 63
Sector size:  512.00 Byte
Cylinder size: 16,065 Sectors
Primaries/Max: 1/4

One partition is defined:  /dev/sda1, type=ntfs, size=93.16 GiB, flags=boot (note it is not mounted)

The image file to be created will be stored on my USB-external 1 TB drive, which KDE PartMan defines as follows:

Device Information:  Generic External (but it is a WD drive, I believe, bought off Ebay)

Path: /dev/sdc
Type: msdos
Capacity:  0.91 TiB
Total Sectors:  1,953,520,065
Heads: 255
Cylinders: 121,601
Sectors: 63
Sector Size: 512.00 Byte
Cylinder Size: 16,065 Sectors
Primaries/Max: 2/4

Several partitions are defined on this drive, as follows:


```
Partition          Type    Mount Point    Size        Used       Flags
---------------  -------  --------------  ---------- ---------- -------
/dev/sdc1           ntfs  /media/WD 1TB   745.06 GiB 134.52 GiB
/dev/sdc2        extended                 186.45 GiB 186.45 GiB
  /dev/sdc5      linuxswap                  1.86 GiB  --
  /dev/sdc6      ext3     /                27.94 GiB   2.78 GiB   boot
  /dev/sdc7      ext3     /home           156.65 GiB   8.17 GiB
```

[the above is not really code, but the formatting system does not seem to present message content properly, such as fixed-pitch fonts for better table presentations]

Note that I run Ubuntu off this drive.  If anyone can see things wrong with this configuration, I would like to know about it (for instance, Ubuntu, booted from GRUB, never seems to come out of hibernate properly).

Anyway, the first partition (/dev/sdc1) is used so Vista can see it and store backups.  Backups are direct copies of my data files, as well as full and incremental Windows system/selected files backups using Acronis True Image.

I would like to use this partition to store the images of the 100 GB drive and later another 80 GB drive for using the forensic tools, in the largely ununsed space of the nearly 750 GB partition.

My command line has been:

$ sudo dd if=/dev/sda of=Cdrive.image
This has been putting the image file in the /home/user space with about 150 GiB free.  the problem is that it stops at about 8 GB copied, and the reason is 'input/output error'  There are bad sectors in the disk of the image being taken.

So I tried:

$ sudo dd if=/dev/sda of=Cdrive.image conv=noerror

But again it stops at 8 GB with the same error and reporting number of "records" in and out.

What should I do to tell 'dd' to image it completely, or should I use another?

---

### Post by zaphod777 on 2009-11-26
it really depends on what kind of image file the program needs. 

I am a big fan of clonezilla you boot with a CD and can write to a USB drive.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by mavigozler on 2009-11-26
> **zaphod777 said:**
> it really depends on what kind of image file the program needs. 

I am a big fan of clonezilla you boot with a CD and can write to a USB drive.

[http://clonezilla.org/](http://clonezilla.org/)

Autopsy/sleuthkit probably are flexible in identifying and working with a variety of image file types.  

However your clonezilla utility home page indicates that it does not copy the unused/free space, so it can't work in my case.  I need the entire disk image as it is, since the free/unused space will be searched for "incriminating" strings as well.

By the way, from the evidence shown by law enforcement, Microsoft products (Windows Live Messenger, Outlook Express/Windows Live Mail) keep a record of everything you do even if you deleted it and told the applications not to keep a record.  Printouts of highly private messages (From/To/Subject) and I think message content have been recovered from the computer even though much of the transaction was done by a web interface.  And I think they are recorded in 'dat' files kept by these Microsoft applications.

My question is "why?".  If the user does not want to keep records of his activities, why would Microsoft keep a record of them???

Microsoft might as well design their applications to send not only messages to the target, but at the same time the 'Send' action is done, send the content also to government agencies (including law enforcement) and spammers, inasmuch as they are keeping tabs on a user's activity even though the user does not want them to do so!  Microsoft seems to be interested in everything BUT maintaining a user's privacy!!!

---

### Post by jacobs444 on 2009-11-26
rememer that the do**ebag police are allowed to LIE!!!!!!!!!!!!!!!!!!!!1

---

### Post by bumanie on 2009-11-26
To clone a hard drive, the best tool would be dd commands.
> dd if=/dev/sda of=/dev/sdbif stands for input file and of stands for output file. Obviously you will have to ensure you have the correct drive names. You also need to ensure the 'of' hard drive The drive you are sending the copy to) has an equal or larger capacity than the 'if' (the drive you are copying from) hard drive. [This site]("http://serverfault.com/questions/4906/using-dd-for-disk-cloning") may help you - there are many others you can find too. dd copies bit for bit, byte for byte.

PS: With what you claim microsoft does - did you ever wonder why the Chinese Government wrote an OS, based on Red Hat, for use on Government computers - they called it Red flag. There was meant to be an English version released, but I've never checked it out.

---

### Post by mavigozler on 2009-11-26
> This site may help you - there are many others you can find too. dd copies bit for bit, byte for byte

Your link actually brought me to some content recommending the use of 'ddrescue', a more persistent application of 'dd'.

I had seen it before, but the explanation of its use was not very clear.  Your link provided more illumination.

I installed the GNU form of it ('gddrescue') although it is invoked from the CLI using 'ddrescue' and its info is set up for 'ddrescue'.

It is indeed a better form of 'dd' for disks with bad/unreadable sectors or otherwise old drives.

The explanation for the command line setup is easy and clear, and if the process is run in the foreground, it nicely shows you how much is read and written, and when it butts up against error-ridden blocks.  The algorithm is such that it makes a real effort to read blocks with errors as much as it can.  Exactly the thing I am looking for.

---

