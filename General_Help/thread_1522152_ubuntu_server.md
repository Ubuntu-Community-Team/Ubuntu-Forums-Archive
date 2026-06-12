---
title: "ubuntu server"
date: 2010-07-01
forum: General Help
---

### Post by hobs2k2 on 2010-07-01
How do I say this.  What I have is a computer running ubuntu server edition, and XBMC.  I also have a torrentflux installation running to download remotely.  I keep all my files on a 1tb external hd so I can move them around.  However, I cannot find a way to move the files from my pc to the external hd.  Ftp won't show the external hd, and neither will doing it manually in the terminal.  Is there a program or server I can run to move them remotely?

Thanks in advance.

---

### Post by cariboo on 2010-07-01
How do you have the usb drive mounted? THe server version doesn't automount external drives like the desktop version. To mount an external drive at the prompt type:

```
sudo mount /dev/sdb1 /media/<somedir>
```

Change the partition to your external drive's partition, and create a directory in /media to replace <somedir> in the example above.

---

### Post by hobs2k2 on 2010-07-01
The pc boots right into XBMC and mounts it automatically.  Is there a way to can get to the terminal remotely while xbmc is ran?

---

### Post by Leppie on 2010-07-01
did you install the ssh server?

---

