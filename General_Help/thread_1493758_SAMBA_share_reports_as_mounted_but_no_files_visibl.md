---
title: "SAMBA share reports as mounted but no files visible"
date: 2010-05-26
forum: General Help
---

### Post by powerpleb on 2010-05-26
In my fstab I have this entry to connect to my NAS box:
```
//192.168.0.1/share /mnt/share cifs   username=user,password=******,auto 0 0

```
For a while it was connecting on startup with no problem (it connects via wifi). But now when I navigate to the directory there is nothing there. 
However if I run mount it reports this:
```
//192.168.0.1/share on /mnt/share type cifs (rw,username=user,password=******)

```
So it seems to be connected and mounted but I can't see any files. Also, if I attempt to unmount it I get:
```
umount2: Device or resource busy
umount: /mnt/share: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy

```
Strangely, it mounts and the files still appear on my other computer. Although, that is connected by ethernet.

Anyone have any idea what is going on?

---

### Post by powerpleb on 2010-05-26
Im pretty sure it's the wireless actually. Trying autofs

---

