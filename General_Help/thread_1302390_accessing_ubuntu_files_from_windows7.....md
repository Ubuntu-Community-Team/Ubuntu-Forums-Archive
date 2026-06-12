---
title: "accessing ubuntu files from windows7...."
date: 2009-10-27
forum: General Help
---

### Post by ninja senses on 2009-10-27
I recently installed a windows 7 partition to my HDD, the problem now is accessing the files.  I need to be able to access them in the zune software so I can add them to my zune.  I had it working on my old xp partition but the software I used(Ext2 Installable File System For Windows) does not work with windows 7, any help?

---

### Post by Dark_Stang on 2009-10-27
[http://www.fs-driver.org/](http://www.fs-driver.org/)
It says it works with Vista... 7's kernel is pretty much the same so it should work with that too.

---

### Post by Bucky Ball on 2009-10-27
You are heading to a dark place. You are MUCH better off to create a shared partition that both OSs can read without the use of smoke and mirrors. Make an NTFS or FAT32 Zune partition that can be easily seen from both OSs.

:)

---

### Post by darkksyde on 2009-10-27
Right click the folder you want to share and click share folder then select samba share

---

### Post by OpenGuard on 2009-10-27
> **darkksyde said:**
> Right click the folder you want to share and click share folder then select samba share

You missed the point .. he's dual-booting.

---

### Post by ninja senses on 2009-10-28
> **Dark_Stang said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)
It says it works with Vista... 7's kernel is pretty much the same so it should work with that too.

I tried this and I got some error message...dont know it off the top of my head.

---

### Post by murderslastcrow on 2009-10-28
The software is likely incompatible with the new kernel in Windows 7 (MinWin rather than QDOS). Your best bet is to make an NTFS or FAT32 partition to share your files between the two. This will also be much faster.

Also, if you're a real masochist, you can just keep all your music files on the Windows 7 drive and make it large enough to hold them, reading them from the mounted NTFS drive every time you boot into Linux.

---

### Post by Bucky Ball on 2009-10-28
> **murderslastcrow said:**
> Also, if you're a real masochist, you can just keep all your music files on the Windows 7 drive and make it large enough to hold them, reading them from the mounted NTFS drive every time you boot into Linux.

That will also work but is clumsy. With Windows best to have the OS on a partition by itself so when it completely screws and you need to reinstall you just kill that partition and start again without having to bother with endless backups.

I go with this philosophy regardless of OS but especially applicable to Windows as a reinstall is needed every now and then to get things ticking over again.

---

