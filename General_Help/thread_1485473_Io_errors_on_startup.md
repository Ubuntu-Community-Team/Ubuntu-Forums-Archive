---
title: "I/o errors on startup"
date: 2010-05-16
forum: General Help
---

### Post by duke.tim on 2010-05-16
I just tried using rootstock to make a ubuntu rootfs,(using the gui) and I set it to a SD card, it didn't write to the SD card but seems to have messed up my card reader. When it finished I had a 1gb drive appear that couldn't be mounted...I now get i/o errors at startup 
```
end_request IO error,dev sdb, sector 0
buffer IO ERROR on device sdb logical block 0
....a few similar errors on diffrent sector's and blocks....
bunch of End request errors.
```

sdb is the location of my generic card reader

so any ideas on whats wrong and how to fix it, I thought it might be related to fstab because of the drives that mounted after rootstock but nothing unusual in it ?

---

### Post by duke.tim on 2010-05-22
Several reboots seem to have fixed this issue...

---

