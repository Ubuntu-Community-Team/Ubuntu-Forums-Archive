---
title: "Changing Permissions"
date: 2011-05-11
forum: General Help
---

### Post by Th3Blaze on 2011-05-11
Before you ask, yes I have looked if it has already been posted and I could not find what I was looking for .
Im trying to change permisions of my SD that usually works but for some queer reason won't work.
It will usually let me add, delete files but this time it won't.
Im guessing its something to do with the permissions, correct me if im wrong.

I want to use the terminal as its quick, so im looking for a command.

Thanks In Advance:confused:

---

### Post by seawolf167 on 2011-05-11
If you are having trouble creating/deleting files and folders, add a *sudo *in front of the command

```
sudo rm [I]filename
[/I]sudo gedit *filename*
```

To change permissions, use [I]chown

[/I]```
man chown
```

Things like executable bits are changed with [I]chmod

[/I]```
man chmod
```

---

### Post by WorMzy on 2011-05-11
What filesystem does it use? If it's FAT or NTFS, then it won't support Linux file permissions, never has done, never will do, but there are methods to get around that.

If it's something other than those two filesystems, then you should be able to just use chown/chgrp/chmod to set the owner, group, and permissions like normal.

Report back with which filesystem it uses and I'll go into more detail regarding it.

```
sudo blkid -c /dev/null
```
should give you an indication of what it is.

---

### Post by Th3Blaze on 2011-05-11
Erm here's all I can find out and it doesnt appear to be working.

```
 th3blaze@janus:~$ chown th3blaze /media/Wii
chown: changing ownership of `/media/Wii': Read-only file system

```

---

### Post by Th3Blaze on 2011-05-11
Oh sorry 

```
 th3blaze@janus:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="91cafa31-65b2-42bf-b88d-847025ad90b7" TYPE="ext4" 
/dev/sda5: UUID="f6a55fcf-a33c-4951-8846-9a3b60e4e9ac" TYPE="swap" 
/dev/sdb1: LABEL="Wii" UUID="EEE1-0AAC" TYPE="vfat" 
 
```

I dont mind formatting it by the way .

I'll give you more detail;

the folder i want permissions for is /media/Wii

my user name is th3blaze

the SD card is fat32

---

### Post by WorMzy on 2011-05-11
> **Th3Blaze said:**
> Erm here's all I can find out and it doesnt appear to be working.

```
 th3blaze@janus:~$ chown th3blaze /media/Wii
chown: changing ownership of `/media/Wii': Read-only file system

```

That may be an indication that you've "locked" the SD card. Check the card for a switch, and flip it, then try again.

---

### Post by WorMzy on 2011-05-11
> **Th3Blaze said:**
> Oh sorry 

```
 th3blaze@janus:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="91cafa31-65b2-42bf-b88d-847025ad90b7" TYPE="ext4" 
/dev/sda5: UUID="f6a55fcf-a33c-4951-8846-9a3b60e4e9ac" TYPE="swap" 
/dev/sdb1: LABEL="Wii" UUID="EEE1-0AAC" TYPE="vfat" 
 
```

I dont mind formatting it by the way .

If you're using it in your Wii, chances are it *has* to be FAT for the Wii to use it. Check the lock switch (if any), and let us know if it doesn't help.

---

### Post by Th3Blaze on 2011-05-11
Yeah it has a lock switch ( which isnt on ) and im going to try reformat it.
Any other idea's if that fails ?

---

### Post by Th3Blaze on 2011-05-11
How queer, it works ?
Thanks anyways ! :)

---

