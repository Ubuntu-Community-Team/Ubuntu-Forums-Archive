---
title: "Need Help - Ubuntu11.10 + Win7 No dual boot / data lost ?"
date: 2011-12-27
forum: General Help
---

### Post by hemant.borse on 2011-12-27
Hi Experts,
I am newbie , wanated to learn some stuff in linux ,I used USB stick to install Ubuntu11.10 on my laptop having win7 on it.
I did take backup of data (unfortunately this was not complete backup) , before installing Ubuntu.
 
Installation of Ubuntu was successful , however , after installation I found that there is no windows 7 anymore on the laptop as second OS also I lost my remaining data.
I completely agree with the guys who think that I should have taken complete backup before messing it up :( . ( I paid cost of being overconfident and learnt a lesson now ) 
 
I remember , I choosen third opion while installing Ubantu "Something Else" . Then I creted a 20 GB partition (with option at begining) and 10GB swap patition (at begining).
 
Can anybody please help me to identify , if I can stll make my laptop as dual os boot OR
I have completely lost my data + Win 7 ?
Is there any way to recover the data?
 
Thanks,
Hemant

---

### Post by xyzzyman on 2011-12-27
Did you resize the NTFS partition before creating new Ubuntu partitions? Sounds like you deleted it instead. If so you probably over wrote Ubuntu right over the top of 4-6gb's of data. Or you're super lucky and the partition is there but you aren't seeing it. 

As long as you don't continue to use or write on the drive you might be able to restore some of the data (
As Windows 7 is 13-16gb's on a default install so it may have just been windows files over-written.  Booting from the live cd can copy/paste the results from:

```
sudo fdisk -l
```

That will list your partition table for us.

Also what sort of files do you need to try to recover? Most likely file names are lost but if they are JPG's and word documents and they aren't overwritten it's still good. Odd files like gave saves, etc... Not so much, at least using the tools available to general public.

---

### Post by hemant.borse on 2011-12-27
> **xyzzyman said:**
> Did you resize the NTFS partition before creating new Ubuntu partitions? Sounds like you deleted it instead. If so you probably over wrote Ubuntu right over the top of 4-6gb's of data. Or you're super lucky and the partition is there but you aren't seeing it. 
 
As long as you don't continue to use or write on the drive you might be able to restore some of the data (
As Windows 7 is 13-16gb's on a default install so it may have just been windows files over-written. Booting from the live cd can copy/paste the results from:
 
```
sudo fdisk -l
```
 
That will list your partition table for us.
 
Also what sort of files do you need to try to recover? Most likely file names are lost but if they are JPG's and word documents and they aren't overwritten it's still good. Odd files like gave saves, etc... Not so much, at least using the tools available to general public.
 
Thanks a lot for reply..
I am sure I have overwritten Ubuntu right over the top of 4-6gb's of data..as I can see approx 294Gb of HDD which is blank.I will post the result of sudo fdisk -l after I put the HDD back to my laptop (Right now , my friend is analysing it,with some software..)
I wanted to recover some .java files and .jpg files from HDD.
Thanks once again I appriciate your help..

---

### Post by xyzzyman on 2011-12-27
> **hemant.borse said:**
> Thanks a lot for reply..
I am sure I have overwritten Ubuntu right over the top of 4-6gb's of data..as I can see approx 294Gb of HDD which is blank.I will post the result of sudo fdisk -l after I put the HDD back to my laptop (Right now , my friend is analysing it,with some software..)
I wanted to recover some .java files and .jpg files from HDD.
Thanks once again I appriciate your help..

The .java files may be a problem, but photorec should hopefully be able to get some if not all the jpg's depending on where they were located on the HDD. I've had luck with some other software but they cost $$.

---

### Post by hemant.borse on 2011-12-28
I have attached the result of sudo fdisk -l command ,can you suggest somthing please

---

### Post by oldfred on 2011-12-28
It looks like you selected to install to full drive, not a partitioned install. There is no NTFS partition shown.

Testdisk's photorec will recover data that is not overwritten. It is a long slow process, the larger the drive & the more data you have the longer it takes. You need another drive with enough room for all the recovered data. It just scans drive looking for anything that resembles a file. It does not have file table so it cannot restore file names but will have extensions.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Some other choices, all work by scanning drive but some may see something another does not. Of course you cannot recover from any data that was overwritten by you install.
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Often best to do a full image backup of drive, so you have something to fall back on. The professionals make a bit by bit image and just work on the image.

---

### Post by hemant.borse on 2011-12-28
Thanks a lot,I have started recovery using PhotoRec , I hope to recover maximum data...
I will update the post to [SOLVED]once it is completed.

---

### Post by hemant.borse on 2011-12-29
I could recover almost up tp 50% of data ,Thanks a lot for your help,thread marked as [SOLVED]
 
-Hemant:)

---

### Post by oldfred on 2011-12-29
Glad that helped.

Just to point out good backups are the best insurance as hard drives also fail or other causes can create ways to lose data. I like to regularly copy data to another drive and archive the most important data to DVDs for permanent storage, so if my backup is overwritten with bad data I still have something to fall back on.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

