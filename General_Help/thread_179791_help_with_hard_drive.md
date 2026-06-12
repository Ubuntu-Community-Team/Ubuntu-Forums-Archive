---
title: "help with hard drive"
date: 2006-05-20
forum: General Help
---

### Post by tomslopez on 2006-05-20
I have an external hard drive, I judt formatted and partitioned it as an ext3, now the problem is that the drive has a folder called lost+found and I'm not allowed to delete it or open it, also I'm not allowed to copy anything into the drive, it says I don't have the permission to do this. what can I do?
and another question is there anyway I can chage the name under which the drive appears on the desktop?

---

### Post by Ramses de Norre on 2006-05-20
The lost+found folder is created by the OS, even if you delete it as root it will be remade on every fsck..
To mount it read write do sudo gedit /etc/fstab and add a line like this for it: ```
/dev/hda4       /home               ext3    nodev,nosuid 0       2

```

The /dev/hda4 part will be something else for your drive, but since you've mounted it allready you can find out by entering 'mount' in terminal.
The /home part is the mountpoint, this is a directory you need to create first yourself and under which the drive will be accesable. The name of the mountpoint is the name that appears on the desktop (when the mountpoint under /media/).


Unmount the drive after saving the fstab and the do sudo mount -a to mount all unmounted drives in fstab.

---

### Post by tomslopez on 2006-05-20
I did what you said, I did sudo gedit /etc/fstab and there I added this line:
```
/dev/sda1	/media/usbdisk	 ext3	rw,nosuid,nodev 	0	2
```
then I unmounted the drive and mounted it again using sudo mount -a and the driver appears again but restricting me of any read and write permission.

---

### Post by Ramses de Norre on 2006-05-20
Who's the owner of the mountpoint? Set it to you if it's root. ```
sudo chown -R username /media/usbdisk
```

---

### Post by aaarg on 2006-05-20
tomslopez: i just recently dealt with a similar issue...i added this to my fstab to get it working

/dev/hdb1 /media/shared/ ext3 auto defaults, 0 0 (this is mine, of course you will need to edit the drive name and mount point)

i initially tried to mount it to /home like you are and i could never get it to work....maybe change that also?

dont know if it will help since im a newb, but it worked for me

---

### Post by tomslopez on 2006-05-20
Ok got i working by changing the owner of the mountmoint.
Thanks.

---

