---
title: "Automount and Bind SD card"
date: 2009-10-27
forum: General Help
---

### Post by cantdrive55 on 2009-10-27
I have a 16GB SD card in my Mini 9 formatted as FAT32 and use it in both Windows and Ubuntu and am trying to bind one folder on it to my Documents folder in Ubuntu. I have tried mounting it at boot however it seems that the card reader has not initialized by the time fstab is first run. If I run *sudo mount -a* it runs and works perfectly. Im just looking for a method that would make it so that I dont have to run that each time I login.

This is the line Im using in my fstab file. 
```
/media/datasd/My\040Documents/ /home/jclifford/Documents/ none bind 0 0
```

---

### Post by cantdrive55 on 2009-10-28
My sd controller wasnt initializing by the time the fstab file was being executed so I changed it so that my sd card mounts to /mnt/sdcard/ and then binded to that and its working perfectly.

---

