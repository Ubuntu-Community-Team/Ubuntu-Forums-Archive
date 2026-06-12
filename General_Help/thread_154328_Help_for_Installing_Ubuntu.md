---
title: "Help for Installing Ubuntu"
date: 2006-04-02
forum: General Help
---

### Post by prpandey on 2006-04-02
Hey guys,

I am in the process of installing Ubuntu 5.1 on my laptop.
I have to partitions -- Windows XP Pro on the primary (~45GB) and one designated for Linux (~15GB).

I downloaded the .iso file, burned it to a CD and everything... now I'm in the process of installing Ubuntu.

My problem:

I get to the part where I have to "partition" or so it says by the installer. I already have a partition setup (using Norton Partition). I also see it available during the Ubuntu installation. **However, I cannot choose the 15GB logical partition to install Ubuntu on it. All I can do is edit the properties of it. I currently have it set as NTFS(?) I don't think NTFS is correct. Which filesystem should I use?**

I don't know what to do from there. I see options such

---

### Post by Sutekh on 2006-04-02
[QUOTE=prpandey]My problem:

I get to the part where I have to "partition" or so it says by the installer. I already have a partition setup (using Norton Partition). I also see it available during the Ubuntu installation. [B]However, I cannot choose the 15GB logical partition to install Ubuntu on it.[/QUOTE]I coud be wrong, but a bootable partition, ie the Ubuntu root filesystem, should be on a primary partition not a logical one shouldn't it?  Or is it extended it can't be on?  (Sorry about the bold it won't turn off :()


Edit: I'm pretty sure I'm wrong about that primary partition stuff, maybe someone else can shed some light.


[QUOTE=prpandey]
All I can do is edit the properties of it. I currently have it set as NTFS(?) I don't think NTFS is correct. Which filesystem should I use?[/B]

I don't know what to do from there. I see options such[/QUOTE]
For Ubuntu you should choose **ext3**

---

### Post by zapcojake on 2006-04-02
seems like in order for the Linux partition to be bootable it has to be close to the begining of the disk (I don't remember exactly why) and if you only have 2 partitions on the disk your Linux partiton could be a primary partition.  You also need to create a swap partition which will work as logical.  If you can't get it to work any other way just delete the partition destined for Linux with norton and leave it blank.  Ubuntu will see it.

---

