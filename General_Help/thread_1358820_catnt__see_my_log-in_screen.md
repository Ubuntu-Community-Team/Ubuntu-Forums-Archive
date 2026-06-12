---
title: "catnt  see my log-in screen"
date: 2009-12-18
forum: General Help
---

### Post by mis-understood on 2009-12-18
recently upgraded to 9.10 when i shut mu computer down and restart it boots but i cant see the log-in screen.
i tried to re-boot in recovery mode and it tells me
dev/sdb5 unexpected inconsistency,run fsck manually in maintaintence mode.
unattached inode 229439
CAN ANYONE SAY WHAT AM I TO DO FROM HERE THANKS

---

### Post by blueridgedog on 2009-12-18
Are you in a console after the error?

If so, you can do as instructed with:

```
sudo fsck /dev/sdb5
```

It is complaining that you have errors on the first partition in the extended partition on your second hard drive.  This may be due to a failing disk or due to an improper shutdown.

---

### Post by mis-understood on 2009-12-18
i am gonna try thanks

---

