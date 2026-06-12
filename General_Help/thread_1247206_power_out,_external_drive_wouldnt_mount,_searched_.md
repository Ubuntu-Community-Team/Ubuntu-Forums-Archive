---
title: "power out, external drive wouldnt mount, searched for help but now worse"
date: 2009-08-22
forum: General Help
---

### Post by bodyharvester on 2009-08-22
okay so my external HDD (NTFS) was connected to my netbook (by USB) and when the switch on the plug socket was accidentally pressed it turned off, when i turned it on i plugged the usb back into the netbook expecting it to automatically open the contents in a file browser, after it didnt i began to panic (i have over a hundred gigs of music and important books and stuff) i searched around for answers and found this

[http://ubuntuforums.org/showthread.php?t=951089&highlight=manually+mount+external+hard+disk](http://ubuntuforums.org/showthread.php?t=951089&highlight=manually+mount+external+hard+disk)

using the code "sudo fdisk -l" i located the HDD. its fine, so i follow the rest of that guys code and royally screwed it up, by making the directory "mydisk" and mounting it like that it now claims "mydisk" is its name, my torrents are messed up now, and i cant unmount it coz it says im not root

can anybody help me reset its name to "Local Disk" so my torrents are okay and make it so that you dont need to be root to mount/unmount

thanks, the panic is less now i know i havent lost all the data

---

### Post by michy99 on 2009-08-22
Post the output of```
mount
```

---

### Post by P4man on 2009-08-22
ubuntu won't mount a dirty NTFS volume. Dirty means, it wasnt closed properly. The easiest and safest way to solve this, is connecting the external hdd to a windows machine, boot it, shut it down, and it will be clean. 

If you dont have a windows machine at hand (then one wonders why use ntfs?), you can use ntfs-3g tools to check the drive and if needed, force the mount, but let me know if booting windows is possible or not.

---

### Post by bodyharvester on 2009-08-22
here it is

---

### Post by bodyharvester on 2009-08-22
> **P4man said:**
> ubuntu won't mount a dirty NTFS volume. Dirty means, it wasnt closed properly. The easiest and safest way to solve this, is connecting the external hdd to a windows machine, boot it, shut it down, and it will be clean. 

If you dont have a windows machine at hand (then one wonders why use ntfs?), you can use ntfs-3g tools to check the drive and if needed, force the mount, but let me know if booting windows is possible or not.

its NTFS coz ages ago i tried installing Win7RC on it and never bothered changing the filesystem, must be fragged by now :(, my mate has a vista, i could probably use that to mount it under windows

is ntfs-3g a "sudo apt-get install" thing?

---

### Post by P4man on 2009-08-22
If windows is too hard, you can run ntfsfix

```
sudo apt-get install ntfsprogs
ntfsfix /dev/yourdrive

```

I recommend you go the windows route though. Windows is better at handling ntfs :) And Id also recommend making a backup (!) and switch to Ext3 if you no longer use windows. Linux is better at handling Ext3 :)

---

### Post by bodyharvester on 2009-08-22
> **P4man said:**
> If windows is too hard, you can run ntfsfix

```
sudo apt-get install ntfsprogs
ntfsfix /dev/yourdrive

```I recommend you go the windows route though. Windows is better at handling ntfs :) And Id also recommend making a backup (!) and switch to Ext3 if you no longer use windows. Linux is better at handling Ext3 :)

thanks, could i backup the data using ubuntu onto my mates hard disk (which is almost certainly NTFS)? im not sure if his HD has enough room to backup everything. would a backup be compressed?

is there a program in ubuntu to backup the data, store it on my HD till i get it to his house and then transfer the backup to his HD and then format my HD to ext3 to restore the data?

ive never made a backup, except when i had XP

---

### Post by michy99 on 2009-08-22
To unmount it, enter```
sudo umount /media/mydisk
```

---

### Post by bodyharvester on 2009-08-22
i think i may try the ntfsfix thing, ill try to save what data i can, then maybe format it to ext3, when i had XP my external HD was so fragmented it wouldnt de-fragment:lolflag:

thanks for the help everyone

---

### Post by bodyharvester on 2009-08-22
> **P4man said:**
> ```
ntfsfix /dev/yourdrive
```

it says

joseph@joseph-laptop:~$ sudo ntfsfix /dev/sdc1
Refusing to operate on read-write mounted device /dev/sdc1.

now what? format?

EDIT: i unmounted then tried but it failed

Refusing to operate on read-write mounted device /dev/sdc1.
joseph@joseph-laptop:~$ sudo umount /dev/sdc1
joseph@joseph-laptop:~$ sudo ntfsfix /dev/sdc1
Mounting volume... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Failed to reset $LogFile: Input/output error.
joseph@joseph-laptop:~$

EDIT: restarted the computer, its normal again, external was auto-mounted and is again "Local Disk"
no idea why or what caused it :o

---

