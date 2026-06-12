---
title: "how do i access my ubuntu files from ubuntu live cd?"
date: 2009-11-25
forum: General Help
---

### Post by xxhopingtearsxx on 2009-11-25
How do I access files from an Ubuntu installation from my Ubuntu Live CD?

---

### Post by xxhopingtearsxx on 2009-11-25
bump

---

### Post by raktarok on 2009-11-25
Isn't the partition listed on the Places menu? Or in the Computer Folder?

---

### Post by amauk on 2009-11-25
From the liveCD, open up nautilus and you should see the hard disk partitions

Mount the partitions, and you should have full access to your install

You may need to run nautilus as root to see inside your home folder
(this assumes a non-encrypted home dir)

---

### Post by xxhopingtearsxx on 2009-11-25
> **amauk said:**
> From the liveCD, open up nautilus and you should see the hard disk partitions

Mount the partitions, and you should have full access to your install

You may need to run nautilus as root to see inside your home folder
(this assumes a non-encrypted home dir)

The only thing I see in my home folder is a "ubuntu" folder and thats not it.

---

### Post by bodhi.zazen on 2009-11-25
```
sudo mount /dev/sdxy /mnt
```/dev/sdxy is your partition

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

Mounting options are dependent on the file system, windows and linux files are different.

Either way you should have access with :

```
gksu nautilus /mnt

#or for KDE

kdesu konkorer /mnt
```

---

### Post by xxhopingtearsxx on 2009-11-25
I'm a newbie, so excuse my stupid questions.

Idk what to put for sdxy, and for the life of me I could not understand that link. :[

---

### Post by oldos2er on 2009-11-25
Run the command **sudo fdisk -l** , post the output here. Then  we should be able to help with the mount command.

---

