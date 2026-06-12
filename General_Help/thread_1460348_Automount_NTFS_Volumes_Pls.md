---
title: "Automount NTFS Volumes Pls ?"
date: 2010-04-22
forum: General Help
---

### Post by BLiNOK on 2010-04-22
Hi ,
I am new to Ubuntu. I have a question: is there an easy way to have my NTFS disks (/dev/sda5 and /dev/sda6) mounted each time I startup ubuntu thus removing the password prompt on first usage of the disks ?
I tried using gnome-mount -p /dev/sda5 but it still asked me for a password.
I also tried installing apt-get install ntfs-3g ntfs-config but that tool also didn't do the trick. I will be thankful if someone replies...

---

### Post by rnerwein on 2010-04-22
hi
try following in a terminal type:
sudo mkdir /mynfs5  /mynfs6    ( or any name you want )

you have to edit your /etc/fstab and insert following line ( works for me )
/dev/sda5 /mynfs5 ntfs defaults,auto,umask=000        0    0
/dev/sda6 /mynfs6 ntfs defaults,auto,umask=000        0    0

then type:
sudo mountall
to verify if it works - if yes your partitions will always be mounted at boot
ciao

---

### Post by Morbius1 on 2010-04-22
The way it was done in the olden days was like this:[B]

STEP 1: Find out how the system sees your partitions[/B]

Open **Terminal**
Type **sudo blkid -c /dev/null**

This will output , among other things the following partition that I want to mount at boot:

[COLOR=Blue]/dev/sda1[/COLOR]: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"

**STEP 2: Create a mount point for your partition to live in**

Open **Terminal**
Type **sudo mkdir [COLOR=DarkOliveGreen]/media/WinC[/COLOR]**

**STEP 3: Add a line to /etc/fstab/ to have this partition mount at boot:**

```
[COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkOliveGreen]/media/WinC[/COLOR] ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```Step 4: Mount them by executing the new fstab

Open **Terminal**
Type [B]sudo mount -a
[COLOR=Blue]
BUT, [/COLOR][/B]before you do that let's see what has been done already. Please post the output of the following commands so we can see what's been done:

Open **Terminal**
Type **cat /etc/fstab**
Type **mount**

---

### Post by 2hot6ft2 on 2010-04-22
Welcome to the forum

You already installed it so it should work just go to
System > Administration > NTFS Configuration Tool
only a couple options to check then a couple more more and you're done.

---

### Post by BLiNOK on 2010-04-22
Thank you very much **[rnerwein]("http://ubuntuforums.org/member.php?u=972890")**,**[Morbius1]("http://ubuntuforums.org/member.php?u=982144")** and **_[2hot6ft2]("http://ubuntuforums.org/member.php?u=568708")_** all for your fast and kind replies... I managed to fix it here is what I did (roughly) :

1)first i wrote in terminal apt-get install ntfs-3g ntfs-config

2)then i saw what was written at top in the location bar when i clicked on one of NTFS Drives; mine were /media/A40601010600D5E8 and /media/26FCD018FCCFE063 (I have no idea why)

3)I wrote in terminal sudo mkdir /media/A40601010600D5E8 and sudo mkdir /media/26FCD018FCCFE063

4)i saw if they were indeed there by clicking on filesistem drive /media

5)i wrote sudo -s to start as superuser

6)i wrote ntfs-config

7)This time a different screen poped up asking me to write a mount point I clicked on it and wrote local disk D and local disk E and clicked apply

8 ) Then I clicked on both checkmarks enable write support for internal and external drive

9) I restarted and this time no password was needed to enter the ntfs drives

---

### Post by Morbius1 on 2010-04-22
> Then I clicked on both checkmarks enable write support for internal and external drive
That's why I never use ntfs-config. Does ntfs-config not know that write support is enabled by default? And why doesn't it know?

The only advantage to ntfs-config is that it's not PysDM :)

Anyway, whatever works.:wink:

---

### Post by krige on 2010-04-23
> **2hot6ft2 said:**
> System > Administration > NTFS Configuration Tool
only a couple options to check then a couple more more and you're done.

I didn't find any automount options, only options to enable writing, but writing was already enabled on my drives by default.

---

