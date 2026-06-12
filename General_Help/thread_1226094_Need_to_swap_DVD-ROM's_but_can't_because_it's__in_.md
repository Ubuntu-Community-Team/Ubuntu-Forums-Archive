---
title: "Need to swap DVD-ROM's but can't because it's  in use!"
date: 2009-07-29
forum: General Help
---

### Post by bigpilot on 2009-07-29
Pretty stupid problem I'm having. I'm trying to install X-Plane 9 off a DVD and it's telling me to insert DVD number 2....but I can't since the disc won't eject because it's still in use.

I find this to be a dumb design in Linux. Do I need TWO drives to install software on Linux or something?

Can someone suggest a remedy?

---

### Post by Psycho.mario on 2009-07-29
Try:
```
sudo umount /dev/sr0 && eject
```(It might not be /dev/sr0, run 'mount' and it should tell you what is mounted on the cdrom (usually /media/cdrom) then umount that)

---

### Post by nikhilk on 2009-07-29
How about
```
sudo eject
```

Does that eject the DVD from the drive?

---

