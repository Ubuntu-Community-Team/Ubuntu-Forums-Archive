---
title: "'Found serious errors... '' message on autumatic disk scan"
date: 2010-06-10
forum: General Help
---

### Post by mahela007 on 2010-06-10
The last few times, I booted ubuntu, the automatic disk check ran and told me that there were "serious errors on /". This had happened once before but that time, I found nothing wrong on booting into ubuntu. However, this time, the scan doesn't seem to progress any further after detecting the error. What is the problem?

---

### Post by plucky on 2010-06-10
> **mahela007 said:**
> The last few times, I booted ubuntu, the automatic disk check ran and told me that there were "serious errors on /". This had happened once before but that time, I found nothing wrong on booting into ubuntu. However, this time, the scan doesn't seem to progress any further after detecting the error. What is the problem?

You should boot the Live CD and run this command from a terminal on the offending partition.
```
sudo e2fsck -C0 -p -f -v /dev/sdax
```

Where x=partition number for your / partition.

Good Luck

To find out the meaning of the options use **man e2fsck** in a terminal.

---

### Post by mahela007 on 2010-06-11
I don't have the 10.04 live CD. Is it ok to use the 9.10 live CD? also, why is it that I can still run my system even with these 'serious errors' ?

---

### Post by ambroseya on 2010-06-11
I'm not sayin' this is what's happening to you but I got "serious errors" and blew it off. 

And a week later, my hard drive failed, and I had failed to use the warning signs to back up ... So my first reaction to something like that? Assure my backups are in order. (Something was against me that week - in a couple days I lost 2 different hard drives and an online server that was due to someone else's negligence, and lost my backups at the same time. sigh).

---

### Post by plucky on 2010-06-11
> **mahela007 said:**
> I don't have the 10.04 live CD. Is it ok to use the 9.10 live CD? 

Should be ok to run from the 9.10 Cd.

> also, why is it that I can still run my system even with these 'serious errors' ?

Just see what it finds and hope it is not the disk going bad.
Could be that either a program data or program has become corrupt and you wouldn't notice until you run the program and it crashes.

Good Luck

---

### Post by mahela007 on 2010-06-11
Thanks... fortunately, I don't use Ubuntu on a "critical" system so even if things do go horribly wrong, it won't cause too much damage. I'll post back once I run e2fsck

---

### Post by dino99 on 2010-06-11
maybe its time to clean the system with gconf-cleaner and bleachbit

---

### Post by mahela007 on 2010-06-12
```
sudo e2fsck -C0 -p -f -v /dev/sda6
                                                                               
  212457 inodes used (24.66%)
     239 non-contiguous files (0.1%)
     269 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 186270/140
 1488557 blocks used (43.25%)
       0 bad blocks
       1 large file

  153491 regular files
   26238 directories
      68 character device files
      26 block device files
       0 fifos
     515 links
   32617 symbolic links (25935 fast symbolic links)
       8 sockets
--------
  212963 files
```
Well, that's the output of the fsck commaand. 
By the way, what's gconf cleaner and bleach-bit?

---

