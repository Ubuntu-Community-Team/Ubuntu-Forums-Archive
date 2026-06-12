---
title: "External HD mounting at  hex encoded mount-point"
date: 2009-12-08
forum: General Help
---

### Post by peterx14 on 2009-12-08
Hi all,

I have an external WD MyBook HD that I use for backups. I use a script to rsync to /media/disk/ but it is no longer mounting at that point, and is instead mounting at a (presumably) random hex encoded directory under /media/.

I'm 90% sure it didn't do this when I first upgraded to 9.10, so I think something must've changed!

Anyone got any ideas?

TIA.

---

### Post by Dennis N on 2009-12-08
Give the mounted partition on the external drive a label. The drive will then mount at /media/label consistently.

See:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

and look at: Contents > Changing the Label

Note: 'Changing' also covers creating one.

---

### Post by peterx14 on 2009-12-09
Thank you - that's perfect!! :D

For the benefit of anyone else, my external drive was formatted as ext3 so I used the following (after unmounting the drive first!):
```

$ sudo e2label /dev/sdb1 MyBook

```
And now when I plug the drive in, it mounts at /dev/MyBook which is perfect.

Thanks again,

Peter.

---

