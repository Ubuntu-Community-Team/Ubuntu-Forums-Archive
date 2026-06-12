---
title: "Urgent! Linux wont boot! :( Freezes at boot screen!"
date: 2009-10-10
forum: General Help
---

### Post by mac666 on 2009-10-10
Hey
Im trying to get into my ubuntu x64:(
how ever i get this error (sometimes):
```
crc error
system halted
```
Sometimes i get pass that screen but then it freezes the second the ubuntu loading screen starts to "move" 
Before i got these errors the computer freezed in ubuntu...

Im now on ubuntu x32, on the same harddrive but on a different filesystem and different installation, and i works, so its not the harddrive faulting.


When i go to recovery, i get this error:

```

///
init: Error parsing configuration: Stale NFS file handle
Kernel panic - not synicing: Attempted to kill init!
///

```

I can explore the filesystem that the x64 is on without problems....
Anyone? :|

---

### Post by mharrison on 2009-10-10
I've not had this problem, but a bit of Google searching found me at this page:  [http://www.articlealley.com/article_941641_11.html](http://www.articlealley.com/article_941641_11.html)  Might be a good read, they have some possible solutions to try.

Sorry I couldn't be of more help.

---

### Post by mac666 on 2009-10-10
```
Use Live CD to boot your system. After this, you need to copy the kernel image from the bootable disk and delete the existing kernel image. Rename the copied image to the one that boot loader recognizes. If you use LILO (LInux LOader), you should run /sbin/lilo to translate present location of copied image to disk geometry language and write to partition’s boot sector.
```


What do they mean? :|

How to copy the kernel? I would be suprised if their would be a file named kernel at the desktop, ready to be copied into my filesystem, somehow and somewhere? :)

---

### Post by Zoot7 on 2009-10-10
A bad hard drive is most likely the cause of a CRC error. CRC errors don't normally happen by themselves, first thing's first: backup up your data, a liveCd is probably the best way to do so.

Then I'd run a file system check (again with the liveCD)
```
fsck -y /dev/sdX
```

Where /dev/sdX is the partition Ubuntu is installed on.

---

### Post by mac666 on 2009-10-11
The partition seemed to be a EXT3/EXT4 partition...
Is it possible to converit it?


EDIT:
This is what i get:```

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda7: rent, 216517/9486336 filer, 13903078/37935473 block

```

rent = Clean

---

