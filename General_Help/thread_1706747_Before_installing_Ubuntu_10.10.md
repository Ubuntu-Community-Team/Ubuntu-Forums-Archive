---
title: "Before installing Ubuntu 10.10"
date: 2011-03-14
forum: General Help
---

### Post by Abhi85 on 2011-03-14
Hey,

Do I need to completely format my drive to install or can it be installed in an existing drive (with files and folders)?

Cause at the moment, when I am trying to install, its asking me to partition and stuff. Can someone please shed some light on this?

Regards.

---

### Post by 3Miro on 2011-03-14
You will need to use at least one partition formated in ext4 (Linux file system). It is recommended that you get another partition for swap.

Before you format/change partitions, backup everything important so that you don't lose stuff if something doesn't work right.

---

### Post by Abhi85 on 2011-03-14
> **3Miro said:**
> You will need to use at least one partition formated in ext4 (Linux file system). It is recommended that you get another partition for swap.

Before you format/change partitions, backup everything important so that you don't lose stuff if something doesn't work right.

Alright, I will try that. Thanks mate.

---

### Post by Abhi85 on 2011-03-14
Sorry to double post, but had a doubt before I start the installation. I have my Win XP on C: and I was planning to install it in the drive H which is on another HDD. 

So my question is, Will Ubuntu overwrite the other OS (Win XP) by any chance?

---

### Post by faz. on 2011-03-14
Just make sure you backup your stuff to an external drive.

But if you select the correct drive, Ubuntu won't touch the other (wrong) drive at all, maybe only to edit the boot.ini file.

---

