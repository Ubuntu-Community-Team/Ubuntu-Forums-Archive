---
title: "Fixed mount point for CD/DVD drive"
date: 2010-07-16
forum: General Help
---

### Post by reneMx on 2010-07-16
Hello everybody and thanks for reading.
I'm using Lucid Lynx and i'm wondering if there's a way to use the same mount point for my CD/DVD drive each time i insert one disk,say '/media/cdrom' , as the default behavior is to mount it on /media/LABEL where "LABEL" is precisely the label for each CD/DVD i put inside.

I'm asking this because I've got a huge cd collection and I'm using gnome catalog but i have to change the cd drive mount point location per cd which is very annoying, i've tried other programs but i find the same issue.
 
Sorry if it's a silly question, i'm kind of new to ubuntu and linux in general.

Thanks.

---

### Post by pazuzuthewise on 2011-05-09
bump

---

### Post by pazuzuthewise on 2011-05-09
This is a dirty and impractical solution, but it works.
CD and DVD media will no longer be automonted. 
You will have to mount them manually, either by using the command line 
```
mount /dev/sr0
```
or you could make a launcher for the command above, or you could use a mount manager panel applet (there are several of those; in XFCE I use the "Mount Devices" XFCE applet).

A. To find out as what device is your CD/DVD unit seen:
1. insert a CD/DVD media into the unit, wait for the automount to mount it, then open it in your file browser.
2. Open a terminal and type:
```
mount
```
Look for the line containing the volume label of the disc you have inserted. The /dev/*something* is the path to the CD/DVD device.

B. Backup your existing fstab configuration file:
```
sudo cp /etc/fstab ~/.fstab.backup
```

If your /etc/fstab will get corrupted, you will be able to boot from a live cd and copy it back from the backup.

C. Create the directory that will be used as mountpoint.
I have used /mnt/cdrom0
You could use another directory as you see fit, but it will have to be created as root:
```
sudo mkdir /mnt/cdrom0
```

D. Now you can edit fstab to mount the CD/DVD to a fixed mount point:
```
sudo nano /etc/fstab
```
Write in a new line:
```
/dev/sr0 /mnt/cdrom0 udf,iso9660 user,noauto,exec 0 0
```
*/dev/sr0* is the path to my CD/DVD device. Use the path you have determined by following step A.
*/mnt/cdrom0* is the new fixed mountpoint (use the directory created at step C.).
Now save the modified fstab file by pressing Ctrl+o, then press the Enter key.
To exit the editor, press Ctrl+X

Now restart the system.

To go back to the default mounting behaviour:
```
sudo cp ~/.fstab.backup /etc/fstab
sudo rm /mnt/cdrom0
```
And restart the system.

---

