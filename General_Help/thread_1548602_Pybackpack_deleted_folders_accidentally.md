---
title: "Pybackpack deleted folders accidentally"
date: 2010-08-08
forum: General Help
---

### Post by langmarp on 2010-08-08
by backing up at the first time with Pybackpack, it deleted all subfolders accidentally ](*,)#-o

I have  selected a destination folder on my ntfs external drive, next to my other  backup folders. During the backup the program has replaced/deleted all my  separate backups of the other systems and I have lost over 100 gb data! 
The problem is, that the file backup manager recognized the folders as unnecessary previous backups of the same system
I  have tried NTFS undelete, but it has not seen the files. The overwritten  folders are in the increments folder, but without the files.

Please, let me know what to do to recover/undelete my folders.

thanks!

---

### Post by KCormier on 2010-08-08
The most important thing to do is unmount your external drive and remount it read only!  The files may not be recoverable, but that will prevent corrupting things any further.

I'll post back with more info in a bit, but you need to unmount it right away.  If you don't know how to mount it back read only, then that's ok, just leave it unmounted.

---

### Post by langmarp on 2010-08-08
yes, i have immediately unmounted it
i am looking forward to hearing from you...
thanks!

---

### Post by KCormier on 2010-08-08
I'm assuming that your drive is currently not plugged into the computer.  The first thing you want to do is disable auto-mounting usb devices.  If it is already plugged in and unmounted, you can skip this step.  If you unplugged it, you don't want it to be mounted read/write (rw) when you plug it in.

[Disable auto-mount for usb storage devices.]("http://ubuntuforums.org/showpost.php?p=4131749&postcount=6")

You shouldn't need to have the filesystem mounted to do any of this stuff.  Just remember to revert the settings above when you're done to turn auto-mount back on.

Install testdisk
```
apt-get install testdisk
```

[Using testdisk to undelete files from an ntfs partition.]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS")

If that doesn't work, you can try photorec which is included with testdisk.  They include a link to instructions on the same site.

Good luck with your data recovery!  Hopefully it wasn't overwritten and you are able to recover it.  If you are able to recover the files, it is very important to test the archives for integrity!  If they were partially overwritten they could be corrupted!

For future notice, whenever you're testing new backup schema, it is never a good idea to do so with your actual backups.  Something a lot of us learn the hard way!

---

### Post by langmarp on 2010-08-09
hi

first of all thanks for you support!

such as ntsfundelete, photorec and testdisk...
any further idea?
maybe through the backup software?

---

