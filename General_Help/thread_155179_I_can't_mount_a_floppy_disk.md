---
title: "I can't mount a floppy disk"
date: 2006-04-04
forum: General Help
---

### Post by rhomsy on 2006-04-04
When I doubled clicked the floppy disk icon in nautalus it said:

Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

What do I do?

Thanks

---

### Post by | MM | on 2006-04-05
I have an issue as well ... just tried to save a file to the fd for the first time and:

```
mount: i could not determine the filesystem type, and none was specified
```

Its just a standard floppy, that i used in windows XP.

If i try and format it i get:

```
Cannot initialise device

Unable to open any device, formatting cannot continue.
```

Anythoughts ... i hope i havent hijacked the initial request.

---

### Post by dmizer on 2006-04-05
remember, if you've created the floppy in windows, that linux doesn't cooperate with NTFS, so if you've formated the disk in NTFS, you will have these problems.

it took me FOREVER to figure out how to format a floppy.  you must have the floppy UN-mounted in order to format it.

---

### Post by | MM | on 2006-04-05
[QUOTE=dmizer]remember, if you've created the floppy in windows, that linux doesn't cooperate with NTFS, so if you've formated the disk in NTFS, you will have these problems.

it took me FOREVER to figure out how to format a floppy.  you must have the floppy UN-mounted in order to format it.[/QUOTE]

So i use 
```
umount /media/floppy0
``` 
to unmount, but whats the command to format?
And the argument to make it fat or fat32 ... so both OS's can read and write.

EDIT:
```
umount: /media/floppy0: not mounted
matthew@ubuntu:~$ sudo mount /media/floppy0
mount: you must specify the filesystem type
matthew@ubuntu:~$

```

---

### Post by dmizer on 2006-04-18
sorry for the terribly long delay in my reply here.  i'd forgotten about this thread.

in case you haven't already found it, there's a handy gui interface for formatting floppies.  i believe that's what i used.  look under applications > system tools ... floppy formatter should be there.  if it's not, you can right click on the application menu to edit the menu and add the formatter to your menu.

however, the only two file systems that offers is fat (not fat32 so it's not bootable) and ext2.

just as a side note, writing floppy img files is the same.  the floppy must be unmounted for it to work.

---

### Post by Ian Maxwell on 2006-04-18
Note that you *probably* don't need to use sudo to mount a floppy. "mount /media/floppy" should work fine and give you more permissions on the disk.

The option for specifying the filesystem type is -t. Try
```
mount -t fat32 /media/floppy
```

---

