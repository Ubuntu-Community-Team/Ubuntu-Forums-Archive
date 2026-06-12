---
title: "Accidentally unmounted drive, needs fix."
date: 2010-12-01
forum: General Help
---

### Post by emoneylovesyou on 2010-12-01
Ive searched the forum and Google with no luck :(

I am using 10.10, and it all started with a drive that disappeared. I tried to remount it, and in the process I unmounted my main Linux drive. I screwed something up trying to use ntfs config. Now when I start up Ubuntu of course it does not work and will only allow me to reach the terminal.

I would like some help remounting the drive so I may use Ubuntu again. Ill provide as much info as I can.

This is for fstab: 
[http://paste.ubuntu.com/538632/](http://paste.ubuntu.com/538632/)

Info pertaining to the Linux drive in fdisk: 
[http://paste.ubuntu.com/538638/](http://paste.ubuntu.com/538638/)

Info for ls /dev/disk/by-uuid/ -n: 
[http://paste.ubuntu.com/538639/](http://paste.ubuntu.com/538639/)

Also my machine is a dual boot with each OS on a separate drive , and a shared drive (the one that disappeared).

---

### Post by ajgreeny on 2010-12-01
Your fstab file should be:-
```
# <file system> <mount point>    <type>  <options>      <dump>

proc    /proc    proc    nodev,noexec,nosuid      0       0
# / was on /dev/sdd1 during installation
UUID=82513d78-0f30-4b4d-b776-05d069138955 /               ext4    errors=remount-ro 0       1
/dev/sdc1        /       ntfs    defaults,nls=ultf8,umask-0222 0 0
/dev/sdc1        /media_ ntfs3-g defaults,locale=en_US.utf8 0 0
/dev/sdd5        none    swap    sw      0       0
```Give that a try and come back again if necessary.

I see your fstab file still has /dev/sdx# notation, which is unusual now as UUIDs are normally used.  I have amended the file to show UUID for the new entry.

---

### Post by Morbius1 on 2010-12-01
For the benefit of those that want to play the home version of this game:

fstab: ( that will never work BTW - I knew ntfs-config was faulty but I'm surprised at this)
> /dev/sdc1        [COLOR=Blue]**/**[/COLOR]       ntfs    defaults,nls=ultf8,**[COLOR=Blue]umask-0222[/COLOR]** 0 0
/dev/sdc1        /media_ ntfs3-g defaults,locale=en_US.utf8 0 0
/dev/sdd5        none    swap    sw      0       0
fdisk:
> Device Boot      Start         End      Blocks  Id  System
/dev/sdd1               1        9599    77096960  83  Linux
/dev/sdd2            9599       10012     3318785   5  Extended
/dev/sdd5            9599       10012     3318784  82  Linux swapPoor man's blkid:
> lrwxrwxrwx 1 0 0 10 Dec 1 06:27 46C07088C070804B -> ../../sdb1
lrwxrwxrwx 1 0 0 10 Dec 1 06:27 48287C7E287C6D36 -> ../../sdc1
lrwxrwxrwx 1 0 0 10 Dec 1 06:27 82513d78-0f30-4b4d-b776-05d069138955 -> ../../sdd1
lrwxrwxrwx 1 0 0 10 Dec 1 06:27 92705187-396c-4f54-89be-ecaa21cbf9b0 -> ../../sdd5
lrwxrwxrwx 1 0 0 10 Dec 1 06:27 CCE4710BE470F952 -> ../../sda1Um ..... Can you get access to whatever partition holds the fstab?

If you can see if ntfs-config had the decency to make a backup copy of it. Maybe something like this:
> /etc/fstab.bakThen copy the backup to it's original name:
```
cp /etc/fstab.bak /etc/fstab
```

---

### Post by emoneylovesyou on 2010-12-01
I can get in to the drive using a live distro. Ill take a look at that, thanks. Although Im not being to hopeful...
ajgreeny , unfortunately my Linux understanding and skills are not to high so I'm not to sure what your post was trying to tell me. again, thanks anyway.

---

### Post by dino99 on 2010-12-01
> **emoneylovesyou said:**
> I can get in to the drive using a live distro. Ill take a look at that, thanks. Although Im not being to hopeful...
ajgreeny , unfortunately my Linux understanding and skills are not to high so I'm not to sure what your post was trying to tell me. again, thanks anyway.

just do:

sudo gedit /etc/fstab

and follow the above posts then modify and save .

---

### Post by ajgreeny on 2010-12-01
> **emoneylovesyou said:**
> I can get in to the drive using a live distro. Ill take a look at that, thanks. Although Im not being to hopeful...
ajgreeny , unfortunately my Linux understanding and skills are not to high so I'm not to sure what your post was trying to tell me. again, thanks anyway.
I was saying that your /etc/fstab file, which you can get to with the live CD to edit should contain exactly what I put in the code box.

The line that was missing was the line for your ubuntu root partition, which is this bit of the code; the rest seemed OK.

```
# / was on /dev/sdd1 during installation
UUID=82513d78-0f30-4b4d-b776-05d069138955 /               ext4    errors=remount-ro 0       1
```My comment about UUIDs was that the fstab file does not normally use /dev/sdd1 notation, but uses UUID=82513d78-0f30-4b4d-b776-05d069138955.

I am not sure about the ntfs partitions as I do not have any or need to mount them, but I admit I did not notice the / mount point of your first ntfs partition sdc1.  You may wish to delete those two ntfs lines for the moment and then they can be added back later, and correct, after ubuntu has booted properly.  If you wish to keep those two entry lines in order to correct them later, just put a # at the start of the them.

---

### Post by emoneylovesyou on 2010-12-01
Thank you all for the help. I was able to edit the fstab file and it fixed everything even my disappearing drive. I learned a lot today and I hope to return the favor to others someday.

---

