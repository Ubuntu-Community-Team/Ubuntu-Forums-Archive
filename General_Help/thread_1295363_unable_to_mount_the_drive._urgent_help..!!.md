---
title: "unable to mount the drive. urgent help..!!"
date: 2009-10-19
forum: General Help
---

### Post by kasrawis on 2009-10-19
i right clicked on my Fat32 partition went to properties in note or advance tab i don't remember the name exactly i've edit something on that and now when i click on drive it says unable to mount the drive  

check this
[IMG]http://i37.tinypic.com/6772pi.jpg[/IMG][B]


Ubuntu 9.04[/B]

---

### Post by Giblet5 on 2009-10-19
Bring up a terminal window and ```
sudo fdisk -l
```

Is /dev/sda6 *really* a FAT partition? If yes, then that partition may be corrupt and you'll have to fix it.

```
sudo dosfsck /dev/sda6
``` *might* be able to correct the file tables.

Are you absolutely sure that it was formatted?

---

### Post by Giblet5 on 2009-10-19
> **kasrawis said:**
> i right clicked on my Fat32 partition went to properties in note or advance tab i don't remember the name exactly i've edit something on that


It would also help a great deal if you could remember (and share) exactly what you edited...

---

### Post by kasrawis on 2009-10-19
> **Giblet5 said:**
> It would also help a great deal if you could remember (and share) exactly what you edited...

thanks for replies and yes i'll exactally tell you what i did but for that take a screenshot of your any partition's properties and post it here i'll tell you what i did and
2 screenshots of diffirent tabs

---

### Post by kasrawis on 2009-10-19
> **Giblet5 said:**
> Bring up a terminal window and ```
sudo fdisk -l
```

Is /dev/sda6 *really* a FAT partition? If yes, then that partition may be corrupt and you'll have to fix it.

```
sudo dosfsck /dev/sda6
``` *might* be able to correct the file tables.

Are you absolutely sure that it was formatted?

i didn't format my partitioin everything is ok in my XP only can't mount it ubuntu

cause i've edit in partition's properties

---

### Post by Giblet5 on 2009-10-19
> **kasrawis said:**
> thanks for replies and yes i'll exactally tell you what i did but for that take a screenshot of your any partition's properties and post it here i'll tell you what i did and
2 screenshots of diffirent tabs

I'm afraid that won't work. See, I have no idea at all what you did (because you haven't told me yet): I don't know what tool you used. I don't know what the FAT partition's properties are *supposed* to be. I don't know if that partition was ever formatted. Etc.

Even if I *did* know what you did, posting what my application looks like won't help you at all.

---

### Post by Giblet5 on 2009-10-19
> **kasrawis said:**
> i didn't format my partitioin everything is ok in my XP only can't mount it ubuntu

**cause i've edit in partition's properties**


How did you edit it?

---

### Post by Giblet5 on 2009-10-19
You can try editing /etc/fstab and seeing if you have an entry for /dev/sda6.

It should look kinda like ```
/dev/sda6 /media/FatFS vfat user,noauto 0 0
```

Then you should be able to mount it by clicking on it in Nautilus (file manager).

---

### Post by kasrawis on 2009-10-19
ok i went to properties of my partition somewhere there was setting there i edit 
 
i wrote what ever was showing in example i only wanted to keep my partition mount forever in my desktop cos whenever i was starting my laptop it was not being mount until i wouldn't click on drive once

and i don't remember what i've write on there if you can send me a properties screenshot then i can tell you what i wrote

thanks

---

### Post by jward3010 on 2009-10-19
Or you can try a "forced" mount. Be cautious about this, doing a forced mount on a badly corrupted volume can cause worse problems although if you're pretty sure everything is fine then go for it.

Actually FIRST try a standard non-forced mount:

Go to a terminal and type:
```

#sudo mkdir /media/fat-volume
#sudo mount -t vfat /dev/sda6 /media/fat-volume
```
If this works try and right-click on drive and get properties, even take picture with Alt+PrntScrn and post here.

If error, try:
```
#sudo mount -t vfat /dev/sda6 /media/fat-volume -o force
```

---

### Post by kasrawis on 2009-10-19
> **Giblet5 said:**
> You can try editing /etc/fstab and seeing if you have an entry for /dev/sda6.

It should look kinda like ```
/dev/sda6 /media/FatFS vfat user,noauto 0 0
```

Then you should be able to mount it by clicking on it in Nautilus (file manager).

it says this 

naseer@naseer-laptop:~$ /dev/sda6 /media/fatFS vfat user,noauto 0 0
bash: /dev/sda6: Permission denied
naseer@naseer-laptop:~$

---

### Post by kasrawis on 2009-10-19
naseer@naseer-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd806d806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         956     7679038+   7  HPFS/NTFS
/dev/sda2             957        4863    31382977+   f  W95 Ext'd (LBA)
/dev/sda5            1849        2868     8193118+   b  W95 FAT32
/dev/sda6            2869        4863    16024806    b  W95 FAT32
/dev/sda7             957        1078      979902   82  Linux swap / Solaris
/dev/sda8            1079        1848     6184993+  83  Linux

Partition table entries are not in disk order
naseer@naseer-laptop:~$

---

### Post by scouser73 on 2009-10-19
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by Giblet5 on 2009-10-19
> **kasrawis said:**
> it says this 

naseer@naseer-laptop:~$ /dev/sda6 /media/fatFS vfat user,noauto 0 0
bash: /dev/sda6: Permission denied
naseer@naseer-laptop:~$

Sorry. I assumed mad Ubuntu skillz. ;)

The procedure would be:

Create a directory for that drive to mount to via ```
sudo mkdir /media/WinDrive
sudo chmod 777 /media/WinDrive
```

Now, edit /etc/fstab via
```
sudo gedit /etc/fstab
```

Look for an entry for /dev/sda6.

Comment it out by putting a '#' at the beginning of that line.

Add a line at the bottom of the file:

```
/dev/sda6 /media/WinDrive vfat user 0 0
```

Save the file and exit gedit.

Make sure /dev/sda6 is unmounted via ```
sudo umount /dev/sda6
```

And mount it via ```
sudo mount -a
```

It should be mounted now, and it will mount at bootup (always mounted).

That assumes that the drive is FAT32... If it's NTFS, change the "vfat" in /etc/fstab to "ntfs".

---

### Post by kasrawis on 2009-10-20
:guitar:thanks for your all helps my problem sloved ;)

---

