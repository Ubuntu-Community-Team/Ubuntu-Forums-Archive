---
title: "automatically mount ntfs drives"
date: 2011-11-28
forum: General Help
---

### Post by sinaphysics on 2011-11-28
Hello,
It's a big problem for me which i can't mount my NTFS drives on my hard drive automatically?
please help me.

---

### Post by searchfgold6789 on 2011-11-28
Automatically. You mean on startup?

---

### Post by sinaphysics on 2011-11-29
yes. on startup

---

### Post by szymon_g on 2011-11-29
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

you're welcome :)

---

### Post by sinaphysics on 2011-11-29
I read the above link. It's a bit complex !
I have 1 drive with ext4 format which is my ubuntu drive. and one is swap and two others are NTFS. now what must I do ?

---

### Post by szymon_g on 2011-11-29
post here whatever 

ls /dev/sd*

gives you /on the gnome-terminal/ :)

---

### Post by sinaphysics on 2011-11-29
/dev/sda  /dev/sda3  /dev/sda5  /dev/sda6  /dev/sda7  /dev/sda8

---

### Post by Mark Phelps on 2011-11-29
That doesn't tell us much.  A better command to use is "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive.

Also, if you are sharing a PC between Win7 and Ubuntu, I would advise strongly AGAINST auto-mounting the Win7 OS partition during startup. This is an easy way to end up corrupting the Win7 OS partition and rendering it unbootable.

---

### Post by sinaphysics on 2011-11-29
the result is 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *        2046   312578047   156288001    f  W95 Ext'd (LBA)
/dev/sda5        82591744   246431743    81920000    7  HPFS/NTFS/exFAT
/dev/sda6       246433792   312578047    33072128    7  HPFS/NTFS/exFAT
/dev/sda7            2048     7813119     3905536   82  Linux swap / Solaris
/dev/sda8         7815168    82587647    37386240   83  Linux



formerly, I had vista but I deleted that partition and installed Ubuntu instead of it. so two of my none-system drives are in ntfs. what do u suggest for mounting them automatically in startup?

---

### Post by sinaphysics on 2011-11-30
and this is my fstab file:

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=2673d4b5-31cb-4f8a-8374-0b189b1b0602 /               ext4    errors=remount-ro 0       1
UUID=eee99285-60cf-4f36-8840-1f3c2e43e464 none            swap    sw              0       0



now what do you suggest? :(

---

### Post by sinaphysics on 2011-11-30
and the uuid:

/dev/sda5: LABEL="New Volume" UUID="EA72E0A172E0742B" TYPE="ntfs" 
/dev/sda6: LABEL="New Volume" UUID="A4B812A2B81272D2" TYPE="ntfs" 
/dev/sda7: UUID="eee99285-60cf-4f36-8840-1f3c2e43e464" TYPE="swap" 
/dev/sda8: UUID="2673d4b5-31cb-4f8a-8374-0b189b1b0602" TYPE="ext4"

---

### Post by Orange_and_Green on 2011-11-30
I would suggest:

1) Backup /etc/fstab (just in case):

```
sudo cp /etc/fstab /etc/fstab_backup
```

2) edit fstab:

```
gksu gedit /etc/fstab
```

and add the following two lines at the end:

```
/dev/sda5 /home/your_user_name/WindowsDisk1 ntfs rw,user,umask=007,uid=0,gid=46,nls=utf8 0 1

/dev/sda6 /home/your_user_name/WindowsDisk2 ntfs rw,user,umask=007,uid=0,gid=46,nls=utf8 0 1
```

NOTE:
* Replace "your_user_name" with your actual user name. Of course, you can change the directory names for the mount points to whatever you like.
* Backing up the data in the partitions before doing this is perhaps not strictly necessary, but it doesn't hurt either.
* EDIT: as oldfred said below, "uid=1000,gid=1000" will give your user ownership of all files in the mounted partition. With "uid=0, gid=46", the owner will be root. Choose what suits your needs best.

Hope this helps, good luck :KS

---

### Post by oldfred on 2011-11-30
These will provide the additional detailed steps:
HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)
Auto mount NTFS Partition
[http://ubuntuforums.org/showpost.php?p=7342606&postcount=10](http://ubuntuforums.org/showpost.php?p=7342606&postcount=10)

Entry in fstab is like this with your UUID & mount you made above:
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0
What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0
EDIT: If you prefer to be the owner then you can also go with this:
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,uid=1000,windows_names 0 0
Hide windows mount with noauto:
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

# use whatever names make sense
sudo mkdir /media/windowssda5
sudo mkdir /media/windowssda6

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# put in your entries with your UUID (preferred or /dev/sdX paths)
# You can copy & paste this into your fstab or adjust paramaters to suit
```
UUID=EA72E0A172E0742B /media/windowssda5 ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0
UUID=A4B812A2B81272D2 /media/windowssda6 ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0
```

---

### Post by rng on 2011-11-30
What should be the options in fstab entry if I want to execute some bash script files from ntfs or fat32 partition?

---

### Post by Orange_and_Green on 2011-11-30
> **rng said:**
> What should be the options in fstab entry if I want to execute some bash script files from ntfs or fat32 partition?

umask=0077, rest as in the posts above

---

### Post by rng on 2011-11-30
And for fat32 partition, I can replace 'ntfs' with 'vfat'. Is that right?

---

### Post by Orange_and_Green on 2011-11-30
> **rng said:**
> And for fat32 partition, I can replace 'ntfs' with 'vfat'. Is that right?

Basically yes, except that for vfat you have to use "utf8" instead of "nls=utf8". Also, for FAT32, you might want to add "shortname=mixed, codepage=850" for short name support.

---

### Post by sinaphysics on 2011-11-30
At last I find a way, I install PYSDM and make both of drives "default"

---

