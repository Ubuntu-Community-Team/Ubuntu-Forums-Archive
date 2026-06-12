---
title: "Samba and ntfs partition"
date: 2006-01-27
forum: General Help
---

### Post by bikeboy on 2006-01-27
I have a file server running Ubuntu and it has an ntfs partition on it. I don't intend on writing to that partition using my Ubuntu desktop. It is there for my Dad's XP computer to write to. I also have fat32 for file sharing but some things I want to keep separate, just for the XP computer.

Is it possible to write to the ntfs partition using the XP computer over samba network share without risking data corruption?

I'm not sure how it works, whether the linux server handles the writing and therefore can't write to ntfs or whether samba relies on the XP computer to write so it occurs natively without the risk.

Any information would be much appreciated, thanks.

---

### Post by Digitallysick on 2006-01-27
i dont think you can write to NTFS from inside linux (i could be wrong, im no expert) but i think ntfs is read only from linux, but fat32 i think is read and write.

---

### Post by bikeboy on 2006-01-27
Yeah I realise that linux itself can't do it, but wondering whether using samba makes a difference because the files are coming from an XP computer but being written to an ntfs partition on a linux computer via samba.

It's confusing to work out whether the linux system itself is responsible for how the data is written to the partition (therefore not allowed) or whether XP/samba is responsible (therefore bypassing the linux kernel's lack of ntfs write support).

---

### Post by Crimguy on 2006-01-28
You need full ntfs support in the kernel.  I think it'll fly.

Personally, I would back the drive up, repartition in ext3 or resierfs, and copy files back over, to be safe.  However, ntfs support has come a long way in teh past couple years.  I've just never had the sac to play with it.

---

### Post by thessem on 2006-01-28
I'm pretty sure Samba doesn't know anything about ntfs, or filesystems at all. Any data being transferred to a linux computer would be written to the harddrives via the drivers that the kernel has installer, meaning, you basicly get read only ntfs.

---

### Post by bikeboy on 2006-01-28
[QUOTE=thessem]I'm pretty sure Samba doesn't know anything about ntfs, or filesystems at all. Any data being transferred to a linux computer would be written to the harddrives via the drivers that the kernel has installer, meaning, you basicly get read only ntfs.[/QUOTE]

Ah thanks for that.

Maybe I should look at removing the ntfs partition and making the fat32 larger until there is safer write support. Part of the idea was to use the server as a backup device for the other computers on the network. I just made the poor assumption that the windows clients would be able to write to an ntfs partition of their own on there.

---

### Post by thessem on 2006-01-28
If you particualy care about the ntfs stuff. the website is [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/). From the looks of it they are not very far away from  stable read/write support.

---

