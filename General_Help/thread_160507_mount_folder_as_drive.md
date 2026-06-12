---
title: "mount folder as drive?"
date: 2006-04-15
forum: General Help
---

### Post by dpsleep on 2006-04-15
hey, i was just wondering if it was possible to mount somthing like
/media/hdb1/Documents\ and\ Settings/Administrator/My\ Documents/My\ Music
as a drive, and if it is, how would i go about that?

---

### Post by trent dillman on 2006-04-15
Have you tried symlinking to /media ?

```
cd /media
sudo ln -s hdb1/Documents\ and\ Settings/Administrator/My\ Documents/My\ Music music
```

---

### Post by dpsleep on 2006-04-15
yes, but its still just a folder, i would like to kinda "emulate" it as a drive

---

### Post by DOtSlaSHuCantCME on 2006-04-15
[QUOTE=dpsleep]hey, i was just wondering if it was possible to mount somthing like
/media/hdb1/Documents\ and\ Settings/Administrator/My\ Documents/My\ Music
as a drive, and if it is, how would i go about that?[/QUOTE]

1.u can goto system/preferences/Administration/Disk

2.found the partition/disk ,where it says "access path" 
use change to pick a point to mount it, (for example create a folder in
home called "tempmount"-->before this step<-- or whatever you would to name the folder ,then use "change" to go that folder(mount point).

in other words mount the disk ,then go to c:/my documents or any other directories youd like. ](*,)  ntfs (xp file system writing to (like saving a file to xp drive/partition) isnt the best but can be done,you can listen to your tunes,look at movies,view documents ,but saving tunes and saving movies to ntfs(xp) will take a little reading and editing your fstab.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

 this should be perfect for you  [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by dpsleep on 2006-04-15
i already have my xp partition mounting as /media/hdb1 in boot, what i want to do is make a "drive" that displays the contents of /media/hdb1/Documents\ and\ Settings/Administrator/My\ Documents/My\ Music

i already did
```
ln -s /media/hdb1/Documents\ and\ Settings/Administrator/My\ Documents/My\ Music /media/music
```
but like a I said, thats only linking the files to /media/music (wich is fine) but i want to then make /media/music appear as a drive.

thanks for the help though

on another note: i know writeing to nfts is experimental or whatever, and that it can corupt your drive. but how big is the risk really?

---

