---
title: "an ordinary question"
date: 2009-09-28
forum: General Help
---

### Post by Banjouser on 2009-09-28
Hi, everybody
I am pretty new in Ubuntu and have a problem. Well. after installing Ubuntu I want to install SuSe in the same partition?
Can you help me to do this without losing Ubuntu?
Chiao,:lolflag:

---

### Post by StuartN on 2009-09-28
> **Banjouser said:**
> I want to install SuSe in the same partition?

No, each operating system must have its own partition. You can share a data partition between different operating systems so that there is only one copy of your data and documents.

---

### Post by nothingspecial on 2009-09-28
> **Banjouser said:**
> Hi, everybody
I am pretty new in Ubuntu and have a problem. Well. after installing Ubuntu I want to install SuSe in the same partition?
Can you help me to do this without losing Ubuntu?
Chiao,:lolflag:

Do you mean same hard drive?

---

### Post by StuartN on 2009-09-28
> **nothingspecial said:**
> Do you mean same hard drive?

A hard disk can contain a number of partitions, each partition can be a different filesystem type (like FAT16 or NTFS or EXT3) and a partition can hold one operating system. To create a multi-boot computer, you would need one partition with each operating system. You can also have some partitions with data and documents, which all the operating systems could access if you wanted.

If you use more than 4 partitions on one hard disk then you have to consider extended and logical partitions as well, but that is not usually a problem.

Some operating systems are very good at detecting what is already installed and creating the extra partition(s) they need to be installed. The Ubuntu installation disk is a good one - which is why people recommend installing Ubuntu AFTER any other operating systems. I don't know how good the SuSe installer is, but there is no reason why you can't have Ubuntu and SuSe multibooting.

---

### Post by shaon3343 on 2009-09-28
**[COLOR=SeaGreen]I dont know about suse but you can try kubuntu or lubuntu , those  works in the same partition. you need to apply these commands in the terminal:[/COLOR]**

for installing lubuntu:     *[COLOR=Red]sudo apt-get install lxde[/COLOR]* 
for installing kubuntu:  *[COLOR=Red] sudo apt-get install kubuntu-desktop[/COLOR]*

---

