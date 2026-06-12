---
title: "auto-mount external drive to folder"
date: 2010-09-26
forum: General Help
---

### Post by ants280 on 2010-09-26
Hello,

The solution may to my problem may exist elsewhere, but I had trouble searching/finding it.

I just bought a new external drive.  The drive is formatted as ext4.  I use it mainly in esata mode.  Whenever I connect it, it mounts to /media/[UUID], where "[UUID]" is the UUID of the drive.  I want it to be located at /media/backup when it is inserted, not in relation the UUID.  I have tried putting a new line in my fstab (mount by UUID to folder) to mount the drive.  It mounts correctly if the drive is connected to the computer and turned on during startup, but if the drive is off/not connected during startup Ubuntu barks at me. (I press 's' to skip mounting the drive)  Is there a way to make external/removable drives mount to a certain location other than /media/[UUID] when they are inserted?  I want the drive to mount to the folder while the computer is running, not only during startup.

---

### Post by linux4me on 2010-09-26
Is [this]("https://help.ubuntu.com/community/RenameUSBDrive") what you're looking for? Since you're dealing with an eSATA drive, I don't know if that's handled like USB or using fstab, but both are described/linked to in that article.

---

### Post by ants280 on 2010-09-26
thanks, but not really what I'm looking for.  I'm hoping to change where the drive auto-mounts without adding it to the fstab. (It looks like the hal daemon chooses where to mount the drive- in this case /media/[UUID]).

Oh, is there a way to add a drive to the fstab without causing errors if it is not present on boot???

[EDIT]
Oh, just add 'noauto' to the options section to the line in fstab where the drive should be mounted.
I also had to add the 'user' option so I could mount it myself.
I still have to click the drive icon in nautilus to mount it, but... meh, not too much extra work.
Oh, here's an excerpt from my fstab (remember: ext4 drive):
```
UUID=159e14f1-5cc8-49a9-b7cf-381984f97f4b /media/backup ext4 defaults,noauto,user 0 2
```

---

### Post by linux4me on 2010-09-27
I was thinking this part is what you were talking about:

> If you are using external disks, you do not usually want to create mount points in fstab, but rather let the hal daemon automount them for you. In this case you can label the partitions instead - see [RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive").

Although you're using an eSATA drive, it is designed for hot-swapping, so it function more like USB?

---

