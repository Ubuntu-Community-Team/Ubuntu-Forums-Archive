---
title: "format USB despite write protection"
date: 2009-10-06
forum: General Help
---

### Post by Hakimjo on 2009-10-06
Hello - I need to reformat a USB drive, but I can't, because there is a write protection issue which is probably described here:
~$ dmesg | tail
[ 6363.642096] sd 6:0:0:0: [sdc] Add. Sense: Write protected
[ 6363.642101] end_request: I/O error, dev sdc, sector 3587840
[ 6363.642105] Buffer I/O error on device sdc, logical block 3587840
[ 6363.642107] lost page write due to I/O error on sdc
[ 6363.643025] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6363.643029] sd 6:0:0:0: [sdc] Sense Key : Data Protect [current] 
[ 6363.643034] sd 6:0:0:0: [sdc] Add. Sense: Write protected
[ 6363.643039] end_request: I/O error, dev sdc, sector 3587856
[ 6363.643043] Buffer I/O error on device sdc, logical block 3587856
[ 6363.643045] lost page write due to I/O error on sdc

I have tried all commands on gparted and things like gtsudo nautilus, force write zeros; and I have checked for a manual switch.  Nothing.  Thanks for sharing the magic command !

---

### Post by Giblet5 on 2009-10-06
What kind of USB drive? CF? SD? Thumb? SSD? Fixed Disk?

If there's no write-protect gadget on the media, it might very well be defective.

---

### Post by wilee-nilee on 2009-10-06
Are you unmounting the usb.

---

### Post by Hakimjo on 2009-10-06
It's a flash drive named: JetFlash TS8GJF2A.  Yes, I unmount it when I can and when required.  I do the same things as with other drives I used before.  E.g. delete the file system with gparted.  It even says that the operation was successful, but then it still has that FAT32 system and exclamation mark.  Same when I move the files to trash in sudo.  It says it will delete them immediately, no error, but in the end, they are still there  I can read the protected files.

---

### Post by Giblet5 on 2009-10-06
> **Hakimjo said:**
> It's a flash drive named: JetFlash TS8GJF2A.  Yes, I unmount it when I can and when required.  I do the same things as with other drives I used before.  E.g. delete the file system with gparted.  It even says that the operation was successful, but then it still has that FAT32 system and exclamation mark.  Same when I move the files to trash in sudo.  It says it will delete them immediately, no error, but in the end, they are still there  I can read the protected files.

 This is a stick/thumb/pen drive. All solid state memory devices are "flash drives", but not all flash drives are sticks.

If the drive is unmounted (doesn't show up in a "df" command), then the drive may be defective.

Early SanDisk Cruzer sticks had this same problem. SanDisk would replace them with only a scan of the store receipt via email.

To check if it's the drive, do this:

```
sudo fdisk /dev/sd???
``` where ??? is the drive letter of your stick.

DON'T SUPPLY A PARTITION NUMBER:
 /dev/sde = correct
 /dev/sde1 = wrong

Enter 'p' and Enter to display the partition table.
Enter 'd' to delete a partition. If it asks for a partition number, enter 2.
Hit the 'p' key and Enter again. Are there any partitions? If so, repeat the 'd' command to delete them.
Hit the 'n' key to create a new partition. Make it a primary partition.
Hit the 't' key to set the partition type:
 83 = ext3 Linux
 c = FAT32
Hit the 'p' key to display the table. Is it correct?
If correct, hit the 'w' key to write out the changes and exit.
Otherwise, hit the 'q' key to quit. It's defective.

If you created a linux filesystem: ```
sudo e2mkfs /dev/sd???1
```

If you created a FAT32 filesystem: ```
sudo mkdosfs /dev/sd???1
```

Where ??? is the drive letter of your stick.

---

### Post by Hakimjo on 2009-10-06
thanks for the detailed instructions.  It worked ... half way.  I did delete the four partitions and it seemed to work as shown by the p command:
Identifiant de disque : 0x6f20736b
Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdd1               1        8064     8257520   83  Linux

But then, when confirming with w, it says:
La table de partitions a été altérée! (the partition table has been modified)
Appel de ioctl() pour relire la table de partitions.
Erreur de fermeture du fichier (error on closing the file)

... hence, still nothing changed, but not exactly the "defective" symptom.  Still some hope ?

---

### Post by dummy910 on 2009-10-06
I ran into a similar situation recently with a thumb drive that had the horrid _U3 isofs_ boot-partition installed on it.

In short, you need to go and get the following [COLOR=red]_U3-Removal-Tool from sansdisk:_[/COLOR]
**[http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)**

_[COLOR=red]Use this tool in windoze[/COLOR]_ to [COLOR=red]wipe the drive clean[/COLOR], then [COLOR=red]reformat it as 16bit FAT[/COLOR](for partitions under 4gigs), then run [COLOR=Red]**[Unetbootin]("http://unetbootin.sourceforge.net/")**[/COLOR] (_in Ubuntu_)to [COLOR=red]install the given .iso.[/COLOR]

Worked for me!

---

### Post by Hakimjo on 2009-10-06
... I tried, but my flash drive is not recognised by the U3 software and I can't sweep it clean.

---

