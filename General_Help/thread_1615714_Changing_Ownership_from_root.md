---
title: "Changing Ownership from root"
date: 2010-11-07
forum: General Help
---

### Post by pbhill on 2010-11-07
I have an external usb hard drive, vfat, mounted as /media/USB STORAGE.
It has on it's own(?) changed it's ownership to root. I need to change it back.
I have tried 'sudo chown -R pbhill : pbhill /media/USB STORAGE' and get the message that *no such file or directory exists*. I can access it read only, so I know it exists. Am I using the correct command?
What goes on here?

---

### Post by sikander3786 on 2010-11-07
> sudo chown -R pbhill : pbhill /media/USB STORAGE

I think you need to put a \ between USB and STORAGE and that serves as space in terminal. So your command should look like

```
sudo chown -R pbhill:pbhill /media/USB\STORAGE
```

---

### Post by ipey on 2010-11-07
use "df -h" to make sure where it is mounted. If it is really mounted on USB STORAGE, I think terminal will understand it as a correct path if you put a backslash after USB (ex: /media/USB\ STORAGE) to signify a space. don't forget that the correct command is 

```
sudo chown -R pbhill:pbhill /media/USB\ STORAGE
```

not

```
sudo chown -R pbhill : pbhill /media/USB\ STORAGE
```

no spaces before and after ":".

edit: oops, slow connection here. I thought there was still no answer.

---

### Post by oldos2er on 2010-11-07
vfat doesn't support Linux permissions, so chown won't work. See [https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32](https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32) and FAT16 Partitions

---

### Post by pbhill on 2010-11-07
[QUOTE=ipey;10084783]use "df -h" to make sure where it is mounted. If it is really mounted on USB STORAGE, I think terminal will understand it as a correct path if you put a backslash after USB (ex: /media/USB\ STORAGE) to signify a space. don't forget that the correct command is 

```
sudo chown -R pbhill:pbhill /media/USB\ STORAGE
```

This command caused a complete scan of the USB drive (about 10 minutes) with the resulting message: Operation not permitted

pbhill@pbhill-Aspire-5670:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.7G  4.7G  4.5G  51% /
none                 1001M  296K 1000M   1% /dev
none                 1006M  268K 1006M   1% /dev/shm
none                 1006M  444K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
/dev/sda5              72G   40G   31G  57% /home
/dev/sdb1             466G  237G  230G  51% /media/USB STORAGE
pbhill@pbhill-Aspire-5670:~$

---

### Post by pbhill on 2010-11-07
> **oldos2er said:**
> vfat doesn't support Linux permissions, so chown won't work. See [https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32](https://help.ubuntu.com/community/MountingWindowsPartitions#FAT32) and FAT16 Partitions

I used FAT 32 for the USB hard drive as I dual boot and access it from both Linux and Windows.

Not to doubt you, but I didn't see anything there about permissions on FAT partitions.

However, I did try a USB thmb drive after reading that, and it is FAT 16. That is also "read only" now. It has my work files on it that were OK on Thursday. What has happened to make my system not want to allow full read/write access to FAT partitions?

---

### Post by oldos2er on 2010-11-08
Look for the section "FAT32 and FAT16 Partitions".

---

### Post by pbhill on 2010-11-08
> **oldos2er said:**
> Look for the section "FAT32 and FAT16 Partitions".

I did. Nothing about permissions. 
However, I'm just going to do a fresh install. Other problems are cropping up, and I need my files!
Now when I try to start various apps I get a "segmentation fault". I think evil spirits have taken over my machine.

---

### Post by oldos2er on 2010-11-09
Vfat partitions don't support Linux permissions; so read/write "permissions" are set when the partition is mounted. The mount commands shown in that URL were examples.

Maybe this will help: [http://ubuntu.swerdna.org/ubufat32.html](http://ubuntu.swerdna.org/ubufat32.html)

---

### Post by pbhill on 2010-11-09
Thanks oldos2er,
After a clean install things are working better but the ownership/permission problem persists. I don't understand what caused theses changes as I've been using this drive for a few years without any troubles. Maybe three years ago or so I used pmount.

That link explains it to me. I think I can figure out how to get it to automount again.

---

