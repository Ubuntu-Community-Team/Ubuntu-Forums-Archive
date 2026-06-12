---
title: "Cant copy files to mp3 player?!?!?!"
date: 2010-03-17
forum: General Help
---

### Post by TheEvilOne6620 on 2010-03-17
I have a Emerson MP3 player its a real cheap piece of garbage but I got it for free so whatever. I want to use it for audio books.

Anyways, when I plug it in and try to copy files to it it says I dont have permission its read only access.

Trying to change the permissions does not work no matter what I try.

I ended up finding out it is formatted as a msdos partition, which from what I read at another web site may be fat16. Dont know for sure about that though, just know it says msdos partition type.

Does anyone know how I can change permissions to this so I can put my audio files on it??

---

### Post by linden940 on 2010-03-17
use a vbox windows to do it....should fix your problem...

dont have a windows disk...well look around for iso torrents...

---

### Post by Chronon on 2010-03-31
> **linden940 said:**
> 
dont have a windows disk...well look around for iso torrents...

Please don't recommend piracy.

OP: What sort of things did you try to do to change the write permissions?  Have you run a fsck.vfat or fsck.msdos on the device (while unmounted, of course)?

---

### Post by t4thfavor on 2010-03-31
Not sure it was recommending piracy, as I'm sure everyone has a COA on some piece of kit they own. Especially if there linux nerds :)

I would attempt to mount it as root, and see if you can move stuff into it via the command line. If you can then you dont have a filesystem problem, just lack of unix permissions to do it.

There is a permissions option you have to set if your going to mount the drive via fstab. I don't remember what it is, but im sure you can find it now that you know it exists.

---

### Post by kokkus on 2010-03-31
> **Chronon said:**
> Please don't recommend piracy.
He didn't recommend piracy.
Torrent is not illegal nor a bad idea.

---

### Post by Chronon on 2010-03-31
Windows disks are copyrighted property of Microsoft.  Distributing ISOs is a violation of copyright, unlike distribution of free-licensed media (GPL, CC, MIT, BSD, etc.).

I use bittorrent too.  I just don't use it for this purpose.

---

### Post by t4thfavor on 2010-03-31
You can get it wherever you want as long as you have a COA. If your doing the downloading, its legal, if your doing the uploading, its not.

That doesn't matter though, as he wont need it for this task.

---

### Post by ubunterooster on 2010-03-31
> **t4thfavor said:**
> Especially if they're linux nerds :)

I would attempt to mount it as root, and see if you can move stuff into it via the command line. If you can then you dont have a filesystem problem, just lack of unix permissions to do it.

There is a permissions option you have to set if your going to mount the drive via fstab. I don't remember what it is, but im sure you can find it now that you know it exists.

gksudo nautilus [opening nautilus as root.]

---

### Post by Chronon on 2010-03-31
> **t4thfavor said:**
> You can get it wherever you want as long as you have a COA. If your doing the downloading, its legal, if your doing the uploading, its not.

That doesn't matter though, as he wont need it for this task.

Well, a torrent involves both uploading and downloading by default.

Anyway, there is absolutely no reason that Ubuntu should have a problem writing files to a UMS device formatted to FAT.  I do this routinely.  If the disk is locked to read-only I would check the integrity of the file system first (as I advised).

---

### Post by 3rdalbum on 2010-04-01
Aww gawd. I never dreamed I'd be the first poster in the thread with the answer.

You have to change the permissions or ownership of the mount point (the directory where the device actually gets mounted to).

Assuming that the mount point is /media/disk (which is often is on Gnome):

```
sudo chmod a+rw /media/disk
```

When you unmount and mount the player again, it should have the correct permissions.

---

### Post by Chronon on 2010-04-01
> **3rdalbum said:**
> Aww gawd. I never dreamed I'd be the first poster in the thread with the answer.

You have to change the permissions or ownership of the mount point (the directory where the device actually gets mounted to).

Assuming that the mount point is /media/disk (which is often is on Gnome):

```
sudo chmod a+rw /media/disk
```

When you unmount and mount the player again, it should have the correct permissions.

That might be the solution, but I have never had wrong permissions set on an auto-mounted directory.  (On Karmic and Jaunty, my audio players always mount to a temporary directory with the name of the volume's label e.g. /media/GIGABEAT)  The OP also said he tried to change the permissions, which is why I wanted further info on exactly what was tried.  Corrupted file system can lead to mounting as read-only too, which was my thought.

---

