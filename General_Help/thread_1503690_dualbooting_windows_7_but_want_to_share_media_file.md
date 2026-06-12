---
title: "dualbooting windows 7 but want to share media files"
date: 2010-06-07
forum: General Help
---

### Post by Confucius_says on 2010-06-07
My main installation is windows 7, I recently  installed ubuntu 10.04 to dualboot it. I've got it up and running, but my goal right now is to be able to easily share media files (pictures, videos, music, documents in my home directory) with windows 7. What I've been doing for the past couple of days is just remounting the "290 GB FIlesystem" device (my windows partition) and finding my stuff in there, but I don't like the idea of having to remount it all the time.

Is there a common way to approach this situation that a lot of people do? I'd prefer to not use some kind of syncing application that always has to be running in the background..

---

### Post by Jose Catre-Vandis on 2010-06-07
Sharing from Windows to Ubuntu is easy, Ubuntu should be picking up your ntfs partition in any case. If not add a command like this to your fstab, after you have created a mount directory.

```
sudo mkdir /media/W7Share
```

Get the UUID for your Windows partition like this:
```
sudo blkid
```

Edit /etc/fstab and add a line like this:
```
#/dev/sda? Windows 7
UUID=DCE08D3CE08D1DC0                           /media/W7Share       ntfs-3g defaults 0 0
```
```
sudo nano fstab
```

Reboot and you should be good to go.

Mounting from Ubuntu to Windows 7 can be more difficult as you will probably have the ext4 file system on Ubuntu which is not natively readable by Windows 7. The easiest way around this is to create a new partition for all your media in ntfs, then both OS can access it.

---

### Post by Mark Phelps on 2010-06-07
> **Confucius_says said:**
> ... Is there a common way to approach this situation that a lot of people do? 

Yes ... the common way is to create a separate data partition, format it using NTFS, and share that.  Since both Ubuntu and MS Windows can read/write NTFS partitions, that makes it simple to share files.

And, before you ask, do NOT attempt to share your /home directory with MS Windows. That is asking for problems.

---

### Post by lancasterjoe on 2013-04-21
What I WAS hoping for was a way of sharing data files. But that seems to be a problem. I have a scanner (~15 years old, and still going fine) but Windows 7 won't recognize it. Ubuntu does, but file sharing seems a problem. Maybe a removable device ;)

---

### Post by oldos2er on 2013-04-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

