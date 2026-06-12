---
title: "Problem with file permissions"
date: 2010-08-10
forum: General Help
---

### Post by jamesgiles on 2010-08-10
Hi,

I recently bought a new 2Tb SATA hard drive, and now want to transfer my files from my old PATA hard drive.

However for some reason the old PATA drive is now read only. It wasn't before, and I'm not sure how/when it changed. I've been searching on the internet and i tried changing permissions using;

 sudo chmod u+w /media/MUSIC_

also

   sudo chmod 777 /media/MUSIC_

neither work, a message just comes up saying read only file system.

How can i change it so I can copy/ delete all the files?


Cheers in advance.

---

### Post by TeoBigusGeekus on 2010-08-10
Try
```
sudo chown yourusername /media/MUSIC_
```

---

### Post by jamesgiles on 2010-08-10
Thanks for your quick reply. It still comes up with the same message however;

chown: changing ownership of `/media/MUSIC_': Read-only file system

and the volume doesn't change.

---

### Post by TeoBigusGeekus on 2010-08-10
Could it be that the drive has errors?
Try
```
sudo umount /media/MUSIC_
```
and
```
sudo fsck /dev/whatever
```

---

### Post by jamesgiles on 2010-08-10
Well I do suspect it's reaching the end of it's life. It was an external drive but I was having problems mounting it so just connected it internally. It's generally been working fine though up until now. I want to transfer everything onto my faster SATA drive though as I've been having problems with the system crashing when loading my music into gmusicbrowser and quad libet.

Here's the output I get from the second command;

fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT

What does it mean there are two FAT's? The drive is one whole drive as far as I can see.

---

### Post by jamesgiles on 2010-08-10
I've managed to get the cut/copy back now using that repair command and chown.

However it still says read only when i go to cut the files to the new drive, but strangely enough they still copy over to the new drive, while staying on the old one.

---

### Post by Vaphell on 2010-08-10
well, it's perfectly logical - you can't modify the old drive's contents and cut+paste = copy+delete. You are allowed to copy but not to delete so it complains about being readonly when you try that.

---

### Post by jamesgiles on 2010-08-11
I think you misunderstand me, what I meant when i said they copy over was that when i cut and paste it actually just copy's them. What's more after that the cut command dissappears from the menu.

---

### Post by Drenriza on 2010-08-11
When you try to transfer files from the ```
/media/drive
``` what commands do you use?

---

### Post by jamesgiles on 2010-08-11
I'm not using the command line, just the GUI, and I was trying cut and paste, but it was disappearing as an option after the first attempt so now I'm just using copy and paste, which is working but now I'll have the problem of deleting the files afterwards. 

I guess I'll give formatting the drive a go once I've moved everything off it.

---

### Post by Drenriza on 2010-08-12
can you try do the command in a terminal
```
whoami
```
post the output here and maybe you can get help before formatting your drive.

---

### Post by jamesgiles on 2010-08-14
Hi It just comes up with my username. 

cheers

---

