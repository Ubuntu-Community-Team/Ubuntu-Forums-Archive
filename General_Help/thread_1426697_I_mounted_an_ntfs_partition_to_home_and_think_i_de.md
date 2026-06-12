---
title: "I mounted an ntfs partition to /home and think i deleted everthing in /home"
date: 2010-03-10
forum: General Help
---

### Post by kybishop on 2010-03-10
If this is the case (that mounting deletes the contents of a destination folder) is there any way to recover any of the files lost?

the exact command I used was sudo mount /dev/sda2 /home

logged out

logged back in

no files.


thanks for your help, kyle

PS the partition the ntfs partition was mounted to is ext3

---

### Post by NightwishFan on 2010-03-10
I suppose it is not your fault if you did not know, but playing around as root is dangerous. You have to fully understand your actions before you sudo anything. I am assuming your data is gone, but I never tried anything so reckless myself. (I am not rebuking you, you had no idea that would happen)

If it is not, then perhaps run a live cd session, and run this command.
```
sudo mkdir /media/test && sudo mount /dev/XXX /media/test
```

Replace XXX with the partition where your /home folder was, then go into /media/test, and see what ya see.

---

### Post by sisco311 on 2010-03-10
If you mount over a non-empty directory, you don't loose your data. 

Unmount the partition & the content of the home directory will be visible again. If you can't unmount it because the device is busy, then reboot.

BTW, you can't keep your home directory on a FAT or NTFS partition, since they don't support UNIX permissions.

---

### Post by NightwishFan on 2010-03-10
Then, yes you are ok. I was hoping so. It might just be confused. Try a reboot or my suggestion to ensure it is there.

---

### Post by Objekt on 2010-03-10
I know that when I mount a disc image (*.iso) to a folder, such as /media/CDROMimage, the formerly blank folder (CDROMimage) becomes filled with the filesystem contained in the image.  If I unmount the image, /media/CDROMimage is empty once again.  But, I haven't tried putting files in the /CDROMimage folder first, then mounting the image.  I didn't know the mount command was destructive.

---

### Post by NightwishFan on 2010-03-10
I do not think it should be, but if your files are gone, it might have messed with permissions or something. Make sure you check if they are there from a live cd like I said.

---

