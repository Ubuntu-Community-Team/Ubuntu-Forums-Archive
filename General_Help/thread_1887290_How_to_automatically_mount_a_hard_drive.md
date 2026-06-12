---
title: "How to automatically mount a hard drive?"
date: 2011-11-26
forum: General Help
---

### Post by sm80 on 2011-11-26
Hello,

I recently installed Ubuntu 11.10 using Wubi.

I am trying to have a hard drive mount on startup.
The drive is at: dev/sdb1: /media/2TB

I was following 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
but the instructions are very confusing.

I was also trying to follow
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
but I don't think thats what I'm looking for since it describes an NFS share, and my hard drive is located in my computer, not remotely on a network.

Is there just a simple command I can enter or something to make this work?

Thanks

---

### Post by sm80 on 2011-11-26
I just saw this thread
[http://ubuntuforums.org/showthread.php?t=1885850](http://ubuntuforums.org/showthread.php?t=1885850)
and installed the NTFS Configuration Tool.

But when I click on it, and type in my password, nothing happens...

---

### Post by Mark Phelps on 2011-11-26
Am I correct in presuming that the partition you want to mount is the one containing Windows?

IF so, do NOT attempt to mount that -- it is already mounted!

Instead, go to /host in your filesystem. The OS partition is already mounted there.

---

### Post by sm80 on 2011-12-10
> **Mark Phelps said:**
> Am I correct in presuming that the partition you want to mount is the one containing Windows?

It is not my Windows drive. Its a separate hard drive that contains all my music, video, etc.

When I open up Banshee and try to play the music, it just sits at "Idle" even after un- and re-mounting the hard drive. This didn't happen last time. Earlier, I would just have to manually mount the drive ever time the system booted up, but now thats not working anymore either...

---

### Post by Mark Phelps on 2011-12-10
If the drive is no longer mounting, and it is an NTFS partition, you could be suffering from the "unclean dismount" problem -- which leaves the NTFS file system in a state that Linux will often not mount it anymore.

What you need to do is connect the drive to a Windows PC and run CHKDSK on the drive.  Then, make sure you "safely remove" it -- don't just unplug or turnoff the drive.

When you then connect it to your Ubuntu PC, it should mount again.

---

### Post by vivace on 2012-04-22
I have the same problem. 

i tried adding : /usr/bin/udisks --mount /dev/sdc1

to my startup commands. i still have to physically click on the drive in nautelous before i can listen to music. I would love for it to be available when i first log in. Cuz its just annoying.

---

### Post by Old_Grey_Wolf on 2012-04-22
> **vivace said:**
> I have the same problem. 

i tried adding : /usr/bin/udisks --mount /dev/sdc1

to my startup commands. i still have to physically click on the drive in nautelous before i can listen to music. I would love for it to be available when i first log in. Cuz its just annoying.

You need to add sdc1 to the fstab file. Instructions at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Mark Phelps on 2012-04-23
> **vivace said:**
> ... i tried adding : /usr/bin/udisks --mount /dev/sdc1

If that is your OS partition, do NOT add it to your fstab.  Automounting your OS partition, as I mentioned earlier in this thread, is asking for trouble.

---

### Post by vivace on 2012-04-26
> **Old_Gray_Wolf said:**
> You need to add sdc1 to the fstab file. Instructions at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

finding these instructions very confusing :frown:

---

### Post by timgood on 2012-04-26
```
sudo apt-get install mountmanager
``` will give you an easy GUI way to do this. Then run the application and set up your hard drive.

Hope this helps.

---

### Post by Morbius1 on 2012-04-26
> **vivace said:**
> finding these instructions very confusing :frown:
```
UUID=DA9056C19056A3B3 /media/DataNTFS ntfs defaults,nls=utf8,uid=1000,umask=000,windows_names 0 0
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/DataExt4 ext4 defaults,noatime 0 2
```Use these as prototypes, adapt them to your own setup, and add them to /etc/fstab. All you have to do is change the UUID number and the mount point:

** To find the correct UUID number for you partitions:
```
sudo blkid -c /dev/null
```** To create the mount point:
```
sudo mkdir /media/Mountpoint
```** When you are finished adding the lines to fstab run the following command to test for errors and if there are none mount the partition:
```
sudo mount -a
```[COLOR=Blue]*Note1: If you create a mountpoint in your home  directory or in /media it will create an icon on the desktop. If you place it anywhere  else it will not.*[/COLOR]

[COLOR=Blue]*Note2: Each mount point must be unique to that partition.*[/COLOR][COLOR=Blue][B]

*BigNote3*[/B][/COLOR]: I don't mount the partition that a WindowsOS lives in. I prevent that from happening by creating a line in fstab that looks like this:
```
UUID=DA9056C19056A3B3 /mnt/WinOS ntfs defaults,noauto 0 0
```If you must mount it then mount it read only:
```
UUID=DA9056C19056A3B3 /mnt/WinOS ntfs defaults,ro,umask=222 0 0
```[COLOR=Blue][I]ro and umask together is somewhat redundant but I'm a suspenders and belt kind of guy.

[/I][/COLOR]

---

### Post by vivace on 2012-04-29
thank you. 

Based on this i added :
```
UUID=B2129DC5129D8ECB /media/Mountpoint ntfs defaults,nls=utf8,uid=1000,umask=000,windows_names 0 0
```

line to fstab and now it mounts on startup. At least i can see that the icon appears. However, i can no longer listen to my music there. It just doesnt seem to respond....

EDIT oops OK i see that my problem is that in Banshee the location for all my music is /media. Not /media/mountpoint. Is there any problem if i just use /media as the mountpoint?

Actually i think i got it working by reimporting all my music from the new location. Thanks!! that was driving me nuts..

---

