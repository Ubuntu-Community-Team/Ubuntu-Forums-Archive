---
title: "Lookin to make Trash Bin for external hdd NTFS partitions"
date: 2009-11-09
forum: General Help
---

### Post by yeeshkull on 2009-11-09
Hi,

Since my external 320 gb USB drive mounts automatically and is not listed in fstab (Ubuntu 9.04), I'm looking for a way to making trash bins for the 2 NTFS partitions I have on this drive.  I set up a ".Trash-1000" folder on each of the partitions but not sure if I should make UUID entries for these partitions in fstab.  Any help would be greatly appreciated.

---

### Post by Giblet5 on 2009-11-09
I can give you a better answer if I know what you want to accomplish vs how you intend to accomplish some mysterious purpose.

You don't want to use Windows filesystems to store Linux files. Even Linux trash. Windows filesystems are very limited and you'll lose file attributes, making recovery difficult and error prone.

---

### Post by yeeshkull on 2009-11-09
> **Giblet5 said:**
> I can give you a better answer if I know what you want to accomplish vs how you intend to accomplish some mysterious purpose.

You don't want to use Windows filesystems to store Linux files. Even Linux trash. Windows filesystems are very limited and you'll lose file attributes, making recovery difficult and error prone.

Thank you for your reply,

The goal is to create a user trash bin for each one of my two NTFS formatted partitions on my external 320gb USB hard drive.  This drive will (now) stay plugged into a dedicated Linux computer and holds personal data files, music and video and I want the file systems to remain NTFS.  I was hoping to not have to pull the files off this drive and have to scramble finding a way to back up all the data, in order to reformat to ext3 or fat32 to get trash bins.

---

### Post by Giblet5 on 2009-11-09
Linux trash bin folders require a linux filesystem in order to preserve file attributes that Windows filesystems don't and cannot store.

That isn't really optional. You can force it to partially work without causing obvious errors, but anything you pull from those trash bins will have wrong permissions, ownership and timestamps. Since it won't work, why bother doing it?

---

### Post by yeeshkull on 2009-11-09
> **Giblet5 said:**
> Linux trash bin folders require a linux filesystem in order to preserve file attributes that Windows filesystems don't and cannot store.

That isn't really optional. You can force it to partially work without causing obvious errors, but anything you pull from those trash bins will have wrong permissions, ownership and timestamps. Since it won't work, why bother doing it?

I see your point, Giblet.  Would your above mentioned explanation, apply to a fat32 file system as well?

---

### Post by Giblet5 on 2009-11-09
> **yeeshkull said:**
> I see your point, Giblet.  Would your above mentioned explanation, apply to a fat32 file system as well?

More so.

Fat32 filesystems don't even store ownership (the one attribute that NTFS can preserve).

The linux filesystem drivers make up default values for missing linux file attributes. That's why 'ls -l' still shows owner and group attributes for files on these filesystems. It's make believe.

It is safe to use these filesystems for limited backups only if you use an archiving mechanism that preserves file attributes. I use tar because it's on every Unix-like system and Winzip and Winrar can read/maintain/write those archives directly. There are lots of others.

---

### Post by yeeshkull on 2009-11-09
> **Giblet5 said:**
> More so.

Fat32 filesystems don't even store ownership (the one attribute that NTFS can preserve).

The linux filesystem drivers make up default values for missing linux file attributes. That's why 'ls -l' still shows owner and group attributes for files on these filesystems. It's make believe.

It is safe to use these filesystems for limited backups only if you use an archiving mechanism that preserves file attributes. I use tar because it's on every Unix-like system and Winzip and Winrar can read/maintain/write those archives directly. There are lots of others.

My needs for this drive are simple.  Of the 320gb I'm looking to do 2/3rds Multimedia and 1/3rd personal storage.  For now, I'll probably keep the larger portion in NTFS (no need for trash on this partition because there is little change on this drive).  The smaller partition I will go with Fat32 (to be able to swap this drive to my Windows PC if needed and to be able to have a trash bin on Linux).

I appreciate your input and interest in my question.

---

### Post by yeeshkull on 2009-11-14
FYI> NTFS trash bin is now supported in new release of Mint 8 (and most probably in Ubuntu 9.10 as well, but I cannot confirm).

---

