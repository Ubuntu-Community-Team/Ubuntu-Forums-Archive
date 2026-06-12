---
title: "ubuntu 11.04 usb external hard drive problem"
date: 2011-08-06
forum: General Help
---

### Post by sblackwell on 2011-08-06
was running mint 10 and upgraded to ubuntu 11.04. my simple drive external hard drive was working great but now I can see the folders that was created but it is telling me they contain nothing. that is not true because it is a 250 gig and i have 190 gig free. when I click properties on hard drive then permission it tells me the permission could not be determined. any clues I have a bunch of files that are important. Thank you

---

### Post by vanadium on 2011-08-06
Post the output of "sudo blkid". This will provide the device name and the file system.

---

### Post by sblackwell on 2011-08-06
/dev/sda1: LABEL="Preload" UUID="AE0831BF083186FD" TYPE="ntfs" 
/dev/sda2: LABEL="SERVICEV001" UUID="20C7-5533" TYPE="vfat" 
/dev/sda5: UUID="986ac282-07df-4c35-ab59-1beacdb0a7d6" TYPE="swap" 
/dev/sda6: UUID="0830964c-9cda-4dfc-81f7-f519456e3c2c" TYPE="ext4" 
/dev/sdb1: UUID="8EF2-A276" TYPE="vfat" 
steven@steven:~$

---

### Post by vanadium on 2011-08-06
My guess is that your vfat file system is damaged. A lot of the data will now be present in so called "unallocated clusters".

vfat (FAT32 in Windows language) is a primitive, old filing system and should not be used for large volumes. It is not robust and highly sensitive to damage.

I am hoping that you have a good backup copy of your important files. You always need this, if your files are important.

A vfat volume can be repaired. However, during the process, the "lost clusters" are converted to files with a random name. With some luck, some of these files represent the intact file. In other cases, the recovered data cannot anymore be used. For this reason, it is much easier to just reformat teh drive and copy the data back from a backup - if you have a backup.

In order to try recovering files (if the need unfortunatelly arises), you can try a couple of things

1) Photorec is a utility that can scan binary data from a corrupt partition (yours is not corrupt - only the file system is) and recognize/recover certain document types, in particular jpeg photos.

2) A vfat system can be "repaired" using either chkdsk in Windows, or dosfsck on a linux system.

First unmount the drive

```

sudo umount /dev/sdb1

```
You can have a diagnosis (not a repair) as following:
```

sudo dosfsck /dev/sdb1

```

In order to perform a repair, you need to supply either the option -a (automatic repair - the utity automatically attempts the best repairing option), or -r (interactive repair - I guess it is safest to add the -f option as well in this case to have the utility save lost clusters into files).

Thus, effective repair could be done using
```

sudo dosfsck -a /dev/sdb1

```
or
```

sudo dosfsck -rf /dev/sdb1

```

---

### Post by sblackwell on 2011-08-06
damn
thank you for the info

---

