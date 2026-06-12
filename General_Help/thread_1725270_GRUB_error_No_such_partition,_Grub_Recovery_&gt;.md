---
title: "GRUB error: No such partition, Grub Recovery &gt;"
date: 2011-04-09
forum: General Help
---

### Post by visevo on 2011-04-09
FYI I've read other posts regarding this topic.

Windows XP was loading very slowly because it originally had a 30gig partition: C drive and a D drive. So I deleted the D drive, which was empty. Now the "C" drive in ubuntu only reads as a 38gig filesystem (when its more like 100) and I get an error after my asus splash that says:

Error, no such partition
Grub Recovery>

So I loaded up ubuntu 10.10 live disk which boots fine. I found a solution here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) but after opening terminal and running
```

sudo fdisk -l

```I get the following
```

ubuntu@ubuntu:~$ sudo fdisk -l

Unable to seek on /dev/sda

```So now I'm stuck. Any suggestions? If I have to reinstall Ubuntu it's fine, it's a pretty fresh installation.

---

### Post by Dans564 on 2011-04-09
it seems you deleted grub and or corrupted it.  I would suggest loading your windows install DVD and deleting the Ubuntu partition.  Then load the Ubuntu disk and reinstall Ubuntu.  If this is a fresh install this isn't a big deal but make sure to backup any data u need from the Ubuntu partition because it will be deleted in the process.

---

### Post by visevo on 2011-04-09
Thanks, I'll give it a shot. Only thing is, I won't be at my house until sunday.

Brings me to another question: It's windows xp service pack 3, does that matter for the recovery disc?

Do you know of any links for a recovery cd download? I can't seem to find any

---

