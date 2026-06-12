---
title: "Switching off disk checking"
date: 2010-07-20
forum: General Help
---

### Post by felix-leg on 2010-07-20
Sometimes when Ubuntu starts, it appears a screen with "Scanning disk in progress. It may take some time". But after it reaches 70% it completely stops, so I have to do a hard restart :(. Can I just switch off this automate? It doesn't help only makes problems. And slows down booting.

---

### Post by dcstar on 2010-07-21
> **felix-leg said:**
> Sometimes when Ubuntu starts, it appears a screen with "Scanning disk in progress. It may take some time". But after it reaches 70% it completely stops, so I have to do a hard restart :(. Can I just switch off this automate? It doesn't help only makes problems. And slows down booting.

Firstly, what you may think is "stopping" may just be normal progress and you are not patient enough.

Check to see if the disk activity light shows any activity at all and give it at least 10 minutes otherwise you risk losing all of your data.

---

### Post by Mark Phelps on 2010-07-21
> **felix-leg said:**
> Sometimes when Ubuntu starts, it appears a screen with "Scanning disk in progress. It may take some time". But after it reaches 70% it completely stops,
More likely, it's found a bad sector and is repeatedly trying to read it, in order to continue the disk check.

>  so I have to do a hard restart :(.
This is defeating the whole value of the disk check -- by terminating it before it can finish.

>  Can I just switch off this automate? It doesn't help only makes problems. And slows down booting.
If you don't let it finish, you're asking for problems later because you probably have a failing hard drive.

---

### Post by felix-leg on 2010-07-22
> **dcstar said:**
> Firstly, what you may think is "stopping" may just  be normal progress and you are not patient enough.

Check to see if the disk activity light shows any activity at all and  give it at least 10 minutes otherwise you risk losing all of your  data.
I'm not unpatient, I've leave it once for more than a hour...


> **Mark Phelps said:**
> This is defeating the whole value of the disk check -- by terminating it before it can finish.
But this is the only way to let it go. If I press "C" before it reaches 70% it abort the check, and do it again on the next boot. If I don't do it the machine just hangs up. But after a hard restart it starts normally, like if a check was done properly. :-s

> **Mark Phelps said:**
> If you don't let it finish, you're asking for problems later because you probably have a failing hard drive.Well, if my fresh less-than-a-half-of-year disk have got an error, I wonder if some software can fix it. Anyway, one question still has no answer: what if it is not just a long-time job, but a real problem?
I wish I would do it manually. Then I could just get "verbose mode" and check what's up :-(

---

### Post by aeiah on 2010-07-22
> **felix-leg said:**
> 
I wish I would do it manually. Then I could just get "verbose mode" and check what's up :-(

well, do it manually then! :p

if it always stops at the same place, it tends to suggest something is wrong. id make sure you've got important stuff backed up, and then do a manual disk check and see if it reports what's wrong. it may not be a physical error with the disk. a 6 month old disk will be under warranty anyway so providing you can back things up, if you do find an error you'll be able to send it back no problem

---

### Post by philinux on 2010-07-22
> **felix-leg said:**
> Sometimes when Ubuntu starts, it appears a screen with "Scanning disk in progress. It may take some time". But after it reaches 70% it completely stops, so I have to do a hard restart :(. Can I just switch off this automate? It doesn't help only makes problems. And slows down booting.

Use recovery mode or the livecd and system>admin>disk utility to manually check the disk.

---

### Post by mcduck on 2010-07-22
> **felix-leg said:**
> 
I wish I would do it manually. Then I could just get "verbose mode" and check what's up :-(

Then why don't you do that? No need to just wish.. ;)

Anyway, is this a fresh new install of 10.04? Have you updated it yet? As 10.04 had annoying bug that caused the process bar on the boot screen to continue showing the fsck in progress even though the disk check was actually already completed. This caused behavior exactly like what you described, fsck going as normally until it froze somewhere after 70% and then took insanely long to finish. Simply updating your system should fix that. 

If that's not the case, then everything would really point towards the drive being close to failing. Use some SMART tool to check it's status. And no, the drive being new doesn't mean anyhting, even the most expensive and brand new hardware can break. And the basic rule for hard drives is that every hard drive breaks, sooner or later..

(It *is* possible to disable fsck on any partition you want to, but it's really something that you shouldn't be doing if you are already having problems with the drive. The whole point of fsck is to make sure your file system doesn't break and you don't loose your files if there are problems with the drive.)

---

### Post by felix-leg on 2010-07-23
> **mcduck said:**
> Then why don't you do that? No need to just wish.. ;)

Anyway, is this a fresh new install of 10.04? Have you updated it yet? 
I have updated *Karmic Koala* into *Lucid Lynx(10.04 LTS)*, and yes the problem came with it. So I'm not sure if I can use my LiveCD for disk check (I still have got *Koala* on it).

---

### Post by mcduck on 2010-07-24
> **felix-leg said:**
> I have updated *Karmic Koala* into *Lucid Lynx(10.04 LTS)*, and yes the problem came with it. So I'm not sure if I can use my LiveCD for disk check (I still have got *Koala* on it).

You can safely use the 9.10 CD,or pretty much any live-CD as long as it contains fsck and support for the filesystem you are using (Ext4 most likely).

---

### Post by felix-leg on 2010-07-29
All right I did it and it tells everything is fine:```
  253644 inodes used (2.69%)
     798 non-contiguous files (0.3%)
     420 non-contiguous directories (0.2%)
         liczba i-w&#281;z&#322;ów z blokami ind/dind/tind: 0/0/0
         Histogram g&#322;&#281;boko&#347;ci fragmentów: 222715/146
 7005905 blocks used (18.56%)
       **0 bad blocks**
       2 large files

  183750 regular files
   26719 directories
      68 character device files
      26 block device files
       0 fifos
    1041 links
   43051 symbolic links (30658 fast symbolic links)
      21 sockets
--------
  254676 files

```However, I have got two partitions. The second one is NTFS, and there is no *fsck.ntfs* for this. Is it possible my problem exists because my system has no tool for checking the second partition?

---

