---
title: "don't want to mount each time i boot"
date: 2010-03-07
forum: General Help
---

### Post by 4techx on 2010-03-07
hi guys,
i'm a newbie to ubuntu and i'm trying to get everything working ok. i have installed ubuntu using wubi and i've found that i can access my files on my windows partition from ubuntu. 

to do this i have to mount the disk and enter the password each time i boot up, and i would like this to be done automatically. i was wondering if this was possible? i put in a link directly to the music folder on windows into my 'places' but it only appears once i have put the password in. its not a huge thing, but its one of those things which would make starting up my ubuntu a lot more conveniant.

---

### Post by The Real Dave on 2010-03-07
You can indeed. You just have to edit your fstab file. 

If you post the output of "sudo fdisk -l" I'll help you set up an automount. :)

To do that, go to Applications>Accessories>Terminal, type it in there, hit enter, give it your password (you won't see the letters come up but they're there) and hit enter again.

---

### Post by 4techx on 2010-03-07
hi, thanks for the reply. this is the output i get:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x675cfa63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020       10258    74212267+   6  FAT16
/dev/sda3           10259       19457    73890967+   7  HPFS/NTFS

---

### Post by nerdtron on 2010-03-07
Or you can use a GUI program, install the ntfs-config tool using synaptic..unmount the windows partition first and then launch the tool and just follow the instructions. This tool works for me. And I'm thankful I don't have to mount each time I restart. I haven't tried on wubi though but I think there won't be any differences.
Good Luck!

---

### Post by The Real Dave on 2010-03-07
> **4techx said:**
> hi, thanks for the reply. this is the output i get:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x675cfa63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020       10258    74212267+   6  FAT16
/dev/sda3           10259       19457    73890967+   7  HPFS/NTFS

First, lets make a folder in which to mount the drive. In terminal again, type 

```
sudo mkdir /media/Windows
```

When the drive is mounted to that folder, it'll appear on your desktop as an icon.


Next type, and give your password to
```
gksudo gedit /etc/fstab
```

You then want to add a line like
```
/dev/sda3 /media/Windows ntfs-3g defaults,uid=1000,umask=0 0 0
```

Save that file and run 

```
sudo mount -v /dev/sda3
```

That will attempt to mount the drive. If you get any errors, post them up. Also, it's possible that we'll need to fix file permissions, so see if you can access/change files on the drive.

---

