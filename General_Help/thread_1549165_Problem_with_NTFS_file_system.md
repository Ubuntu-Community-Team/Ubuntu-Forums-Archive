---
title: "Problem with NTFS file system"
date: 2010-08-09
forum: General Help
---

### Post by Fedx on 2010-08-09
Hi, i have the following problem (Ubuntu Karmic, kernel 2.6.31-16-generic):

when i try to read the windows partition only a portion of the content is readable, many files and directory are inaccessible and a "ls -l" command displays "?" characters instead of file info(permissions, owner, etc).
I have also tried with testdisk, in that case the file system seems to be correctly read(i'm able to navigate all the fs structure).
As result of this problem, windows can't bootup (i suppose grub can't read the NTLDR from the file system).

Any idea?

---

### Post by Mark Phelps on 2010-08-09
If WinXP can't boot into a desktop, there's a good chance that the filesystem is corrupted.  And in that case, Linux won't be able read it properly either.

If you can boot into Safe mode or Command Mode in XP, run chkdsk to attempt to fix the filesystem.

---

### Post by nmaster on 2010-08-09
> **Mark Phelps said:**
> If WinXP can't boot into a desktop, there's a good chance that the filesystem is corrupted.  And in that case, Linux won't be able read it properly either.

If you can boot into Safe mode or Command Mode in XP, run chkdsk to attempt to fix the filesystem.

you can also try fixing the disk in ubuntu.  you'll need ntfsprogs though:
```
sudo ntfsfix /dev/sdaX
```

change sdaX as is appropriate for you.

i recently had a problem with an external ntfs drive and it didn't work on ubuntu but it did work on debian (lenny).  i'm not really sure why, but you should try it.

---

### Post by Fedx on 2010-08-09
Thanks for the replies,
i tried ntfsfix without success, now, as soon as i found my WinXP cd, i try to perform a file system check with chkdsk. Anyway i don't understand why testdisk is able to read the file system correctly...

---

### Post by nmaster on 2010-08-09
> **Fedx said:**
> i tried ntfsfix without success

out of curiosity, what error did you get? i have only needed ntfsfix once before and i was surprised to see it work on debian but not ubuntu.  i'm just wondering what exactly happened for you.

---

### Post by Fedx on 2010-08-09
I get no error, simply i still have my problem :(

 ```

fedx@fedx-ubuntu:~$ sudo ntfsfix /dev/sda1
[sudo] password for fedx: 
Refusing to operate on read-write mounted device /dev/sda1.
fedx@fedx-ubuntu:~$ sudo umount /media/WINDOWS
fedx@fedx-ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
fedx@fedx-ubuntu:~$

```

i misunderstood something about ntfsfix?

---

### Post by nmaster on 2010-08-09
> **Fedx said:**
> I get no error, simply i still have my problem :(

 ```

fedx@fedx-ubuntu:~$ sudo ntfsfix /dev/sda1
[sudo] password for fedx: 
Refusing to operate on read-write mounted device /dev/sda1.
fedx@fedx-ubuntu:~$ sudo umount /media/WINDOWS
fedx@fedx-ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
fedx@fedx-ubuntu:~$

```i misunderstood something about ntfsfix?

oh no, you haven't misunderstood anything.  i had a very different problem than you have. i just figured it would be easier if you could fix the problem through linux, rather than needing windows.  

sorry i couldn't offer more useful suggestions :(

---

### Post by Fedx on 2010-08-09
> i just figured it would be easier if you could fix the problem through linux, rather than needing windows


I think the same!!! ;)

---

### Post by Mark Phelps on 2010-08-13
Contrary to popular opinion, ntfsfix can not fix ALL NTFS problems, only some of them.  If you're lucky and your problem is one of those, then you can fix the NTFS problems from Linux.  IF you're not lucky, then you will have to boot into an MS Windows OS to do the repairs.

---

