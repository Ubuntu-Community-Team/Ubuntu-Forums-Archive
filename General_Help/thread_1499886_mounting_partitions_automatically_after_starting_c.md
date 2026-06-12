---
title: "mounting partitions automatically after starting computer"
date: 2010-06-02
forum: General Help
---

### Post by ranjithnair on 2010-06-02
I want to mount partitions automatically after starting computer....currently i hav to click on the partitions and mount them.....

---

### Post by lukeiamyourfather on 2010-06-02
There's a file that contains all the file systems and what to mount when starting, its /etc/fstab. If you search this forum or the web for /etc/fstab you'll find lots of useful information. Cheers!

---

### Post by WorMzy on 2010-06-02
You need to edit /etc/fstab to make partitions automatically mount. You can edit this file by running ```
gksu gedit /etc/fstab
``` but be warned, messing this file up _will_ cause you problems, so until you know what you're doing, don't edit any of the existing lines, just add new ones at the bottom of the file.

To help you understand what you need to put into the document, please open a terminal and post the output of ```
sudo fdisk -l && sudo blkid
``` (please note that the letter after fdisk is a lower-case L, not an upper case i or a number one.)

Also, if you could tell us which partitions you want to be mounted, that would help too. :)

---

### Post by ranjithnair on 2010-06-03
This is my blkid output plz can u tell me wat to add to fstab.......

/dev/sda1: UUID="a7646169-4bc1-4ffe-a96f-93d143f352b5" TYPE="swap" 
/dev/sda2: LABEL="WINDOWS XP" UUID="EA4442224441F23D" TYPE="ntfs" 
/dev/sda4: LABEL="MOVIES" UUID="58DF-9114" TYPE="vfat" 
/dev/sda5: LABEL="SOFTWARE" UUID="ECF3-D85B" TYPE="vfat" 
/dev/sda6: LABEL="SONGS" UUID="262CEC452CEC121B" TYPE="ntfs" 
/dev/sda7: UUID="413f08de-40b5-4754-a165-0329b62902d1" TYPE="ext4"

---

### Post by WorMzy on 2010-06-03
It depends on what you want to mount, and where you want to mount it.

For example to mount the partition called "MOVIES" to /media/MOVIES, I would add the following to fstab:
```
UUID=58DF-9114 /media/MOVIES vfat defaults 0 0
```

For SONGS, I would add:
```
UUID=262CEC452CEC121B /media/SONGS ntfs defaults 0 0
```

For SOFTWARE:
```
UUID=ECF3-D85B /media/SOFTWARE vfat defaults 0 0
```

And WINDOWS XP:
```
UUID=EA4442224441F23D /media/WINXP ntfs defaults 0 0
```

You may need to create the folders in /media before these partitions successfully automount; so run, in a terminal ```
sudo mkdir /media/MOVIES /media/SONGS /media/SOFTWARE /media/WINXP
```

---

### Post by ranjithnair on 2010-06-07
Thanks....but now when I unmount the drive then i am not able to mount it....also i am not able to mount my pendrive.....

---

### Post by ranjithnair on 2010-06-07
Thanks....but now when I unmount the drive then i am not able to mount it....also i am not able to mount my pendrive.....

---

### Post by sahabcse on 2010-06-07
open the /etc/mtab and and copy the mounted volume entry, then paste it into the /etc/fstab for permanent mount

---

### Post by ranjithnair on 2010-06-07
I am not able to mount my pendrive now....plz help

---

### Post by sahabcse on 2010-06-07
connect the pen drive and paste the o/p of 

tail -f /var/log/messages

---

### Post by ranjithnair on 2010-06-07
Thanks guys for ur help....actually my pendrive got corrupted

---

### Post by ranjithnair on 2010-06-07
This is wat I added to /etc/fstab.........

/dev/sda4 /media/Movies   vfat   user,fmask=0111,dmask=0000   0 0

/dev/sda6 /media/Songs ntfs defaults 0 0

/dev/sda5 /media/Software   vfat   user,fmask=0111,dmask=0000   0 0

/dev/sda2 /media/WINXP ntfs defaults 0 0

**[COLOR="Red"]Now the problem after i unmount any of the drives i cant mount it again..........[/COLOR]**

---

