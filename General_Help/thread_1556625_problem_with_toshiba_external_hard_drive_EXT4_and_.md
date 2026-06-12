---
title: "problem with toshiba external hard drive EXT4 and PS3 FAT32"
date: 2010-08-19
forum: General Help
---

### Post by drillerccg on 2010-08-19
Hi,

To watch movies on an external drive attached to a Sony PS3, a FAT32 partition is required. The problem to convert everything to FAT32 is that I will be limited to only the 4Gig files. This is OK for movies since most are under 4 GB or we can even split them if larger. However, I have img files of for some systems that are larger than 4 GB.

The drive was originally an NTFS system (but was readable in Ubuntu and Windows, have no idea why!!?). What I thought would solve my dilemma was to wipe it off with Gparted and create 2 partitions:

sdb1 FAT32 (changed flag to boot) 350GB for the PS3 movies and,
sdb2 EXT4 (tried EXT2 also) 150GB for my bigger than 4 GB files

the problem is that now I can't write to the EXT4 partition. Can't create folder (right click on it will not have the "create folder" lit up). Is this due to the boot flag on FAT32?

 Any help would be appreciated.

---

### Post by LowSky on 2010-08-19
You shouldn't even have a boot flag if its a storage drive, but its not your issue.

The reason you cannot write or create folders to the EXT4 partition is because you do not have your permissions set correctly. When you created the partition using gParted it set the owner as root. You are going to want t set it to everyone its pretty simple.

Withthe drive pluged in

open a terminal and type

```
gksu nautilus
```

go to the /media folder, were the drive should mount to. right click on the drive's partions name. and change the permissions to allow everyone to access to read and write.

---

### Post by drillerccg on 2010-08-19
> **LowSky said:**
> You shouldn't even have a boot flag if its a storage drive, but its not your issue.

The reason you cannot write or create folders to the EXT4 partition is because you do not have your permissions set correctly. When you created the partition using gParted it set the owner as root. You are going to want t set it to everyone its pretty simple.

Withthe drive pluged in

open a terminal and type

```
gksu nautilus
```go to the /media folder, were the drive should mount to. right click on the drive's partions name. and change the permissions to allow everyone to access to read and write.


I did gksu nautilus, went to /media, right clicked on the drive and then to properties (right?). In the permission tab there is no "everyone" options. 

These are what is listed:
Owner set to root
folder access : create and delete files
file access: ---
Group: root (no choice for everyone, a bunch listed though)
Folder access: access files
Others
Folder access Access files
File access: ---
Execute: not checked
and apply permission to enclosed files

I am using Lucid. Am I in the right place? Thanks for speedy answer.

---

### Post by drillerccg on 2010-08-19
> **drillerccg said:**
> I did gksu nautilus, went to /media, right clicked on the drive and then to properties (right?). In the permission tab there is no "everyone" options. 

These are what is listed:
Owner set to root
folder access : create and delete files
file access: ---
Group: root (no choice for everyone, a bunch listed though)
Folder access: access files
Others
Folder access Access files
File access: ---
Execute: not checked
and apply permission to enclosed files

I am using Lucid. Am I in the right place? Thanks for speedy answer.

I changed owner and group setting  to my username. Now I can create a folder. Is this going to work or do I have to find the everyone option? TIA I'm a newbie to Linux.

---

### Post by drillerccg on 2010-08-20
any help with setting these permissions in Lucid is appreciated. I do not see "everyone" option in nautilus for neither Owner, Group, or Others.

---

