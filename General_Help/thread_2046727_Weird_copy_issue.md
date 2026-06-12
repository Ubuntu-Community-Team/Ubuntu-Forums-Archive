---
title: "Weird copy issue"
date: 2012-08-23
forum: General Help
---

### Post by CrusaderAD on 2012-08-23
I'm running the following command:

```
user@console:~$ cp file123.bak /media/5BE5-A381/file123.bak
```

Which is coping a file to an external hard drive. The result is this:

```
user@console:~$ cp: writing `/media/5BE5-A381/file123.bak': File too large
```

There is plently of space on both the source drive and destination drive. Any ideas?

---

### Post by TheFu on 2012-08-23
A shot in the dark, but could the file system be out of inodes?  Use 
```
 df -i
```
to check.

---

### Post by CrusaderAD on 2012-08-23
> **TheFu said:**
> A shot in the dark, but could the file system be out of inodes?  Use 
```
 df -i
```
to check.

Hm, here's the result:

```
/dev/sdc1                  0       0       0    -  /media/5BE5-A381
```

---

### Post by CrusaderAD on 2012-08-23
I tried using gparted to delete and recreate the partition, it that part worked fine. Still the same issue when coping.

---

### Post by TheFu on 2012-08-23
Here's one from here:
```
$ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda1      884736 414552 470184   47% /
```What file system is on that drive?  Use**  blkid** to determine this.
If it isn't a Linux one (NTFS), then you need to explicitly mount it read-write and setup user/group permissions.

---

### Post by CrusaderAD on 2012-08-23
Hm, it is a linux partition. It lets me copy about 4 gig to the external drive, then dies.

---

### Post by era86 on 2012-08-23
If this is a FAT32 filesystem, there is a 4GB limit on files being stored. You'll need to reformat to NTFS.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;314463](http://support.microsoft.com/default.aspx?scid=kb;en-us;314463)

The link is for Win XP, but has information on the situation I believe you are running into.

---

### Post by TheFu on 2012-08-23
All those zeros in the **df -i **say you are out of inodes. ZERO storage left.  

Are you certain of the type of partition?  **blkid** will prove it. From everything else you are showing, it seems this is not a Linux formatted partition.

You could have USB controller, cable or other hardware issues too. Does **dmesg** show anything funny? What about syslog?

---

### Post by CrusaderAD on 2012-08-23
> **era86 said:**
> If this is a FAT32 filesystem, there is a 4GB limit on files being stored. You'll need to reformat to NTFS.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;314463](http://support.microsoft.com/default.aspx?scid=kb;en-us;314463)

The link is for Win XP, but has information on the situation I believe you are running into.

Doh! That was it! Man I can't believe I didn't see that. Thanks everyone!

---

