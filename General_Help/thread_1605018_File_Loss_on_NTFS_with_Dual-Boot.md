---
title: "File Loss on NTFS with Dual-Boot"
date: 2010-10-24
forum: General Help
---

### Post by TheCosmicFrog on 2010-10-24
Hi everyone,

Here's the breakdown of my Hard Drive:

Partition 1: Windows 7 - **NTFS**
Partition 2: Ubuntu 10.10 - **Ext4**
Partition 3: Data - **NTFS**
Partition 4: Windows Recovery - **meh...**

Basically, I have it so that I have one large NTFS partition (Data) for sharing files between Ubuntu and Windows. It works very well. I keep all my Documents, Music, Pictures and Videos on "Data" and then sym-link those folders to my home folder on Ubuntu. 

Unfortunately, I'm afraid to bootup Windows. Sometimes when I boot Windows, files that I made or edited in Ubuntu get lost, unindexed or corrupt. It happens very frequently with image files (.jpeg, .png, etc.) but also happens with PDFs and folders. 

This means that not only do these files become unusable, but I also can't delete them. Even using *$ rm -rf my_file* returns a "Cannot delete my_file. It is not a file or directory."

The only way to get rid of these files is to perform a CHKDSK on Data when I boot Windows. CHKDSK always finds a shed-load of files that have gone haywire. I'm usually greeted by an seemingly indefinite list of "Removing index entry xyz from $afxyz" and other scary looking actions being taken out on my files.

I keep backups of my files on an external HDD and a remote server, but it's no use when I'm backing up corrupt files. 

Is there a reason why I'm losing so many files when I boot Windows? Is it because I'm using NTFS, or something else I'm doing wrong? I like to think I have a good deal of Linux knowledge, but this one just baffles (and frustrates the hell out of) me.

Or if anyone can think of a better solution to sharing my files between Windows and Ubuntu, feel free to suggest them :)

Cheers,
Aaron

---

### Post by Schrute Farms on 2010-10-24
I can't exactly help you, but I can tell you that I share a FAT and an NTFS drive between Windows and Ubuntu, and I've never had the problems you are having, so something is going wrong with your install.

My first guess is maybe the drive isn't getting un-mounted correctly or at all when Ubuntu shuts down, but I don't have the knowledge to help you with that.  So think of this as a bump...

---

### Post by sikander3786 on 2010-10-24
For me, since ever, the best of sharing data between Ubuntu and Windows has been NTFS. I have had no problems ever.

Check your HDD for bad sectors. Hardware failures might be causing the drive to lose data.

Post the output of

```
cat /etc/fstab
```

So we can have a look at your mounts.

---

### Post by TheCosmicFrog on 2010-10-24
HDD has no bad sectors. Here's the output:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=0cccbb78-9373-45d9-b599-ccc9f9589145 /   ext4    errors=remount-ro 0       1

/dev/sda2 /media/1EFE882CFE87F9F3 ntfs-3g defaults 0 0
/dev/sda3 /media/Data ntfs-3g defaults 0 0
/swapfile none swap sw 0 0


```

---

### Post by TheCosmicFrog on 2010-10-25
Another interesting thing is that whenever I create a Virtual Machine hard drive on my Data partition using VirtualBox the file always gets corrupt after I reboot Ubuntu...

They never get corrupt if I put them in my ~/.virtualbox folder on my Ext4 partition...

---

### Post by I&amp;U on 2010-11-28
hi.
I also have that problem.
I've lost my data several times & I don't know why?
I have a windows XP, Ubuntu 10.10, and two other NTFS drives.
Every thing's Ok but I'm afraid of going to XP because my recently created &/or edited data on the other two drives will be lost.

PLZ help me....
THANK U

---

### Post by TheCosmicFrog on 2010-11-28
> **I&U said:**
> hi.
I also have that problem.
I've lost my data several times & I don't know why?
I have a windows XP, Ubuntu 10.10, and two other NTFS drives.
Every thing's Ok but I'm afraid of going to XP because my recently created &/or edited data on the other two drives will be lost.

PLZ help me....
THANK U

It's recently stopped happening to me. Haven't figured out why though.

---

### Post by I&amp;U on 2010-11-28
> **TheCosmicFrog said:**
> It's recently stopped happening to me. Haven't figured out why though.

But I still have it.
I think it is a problem from nautilus or sth else.
You didn't do anything? But u may still have it. 
It's very deep problem I think because just today I lost two of my new pic folders.

---

### Post by TheCosmicFrog on 2010-11-28
I think it stopped happening after I reinstalled 10.10.

---

