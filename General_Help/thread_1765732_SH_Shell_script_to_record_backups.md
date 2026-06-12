---
title: "SH Shell script to record backups"
date: 2011-05-23
forum: General Help
---

### Post by vascofg on 2011-05-23
Hi, I've previously created a script to backup some iso files to dvd's but had to do a format so lost it.
Back then I used a command prior to growisofs that closed the dvd drive (if opened) and waited until the disk was ready to write before starting growisofs.
I can't find that command now, anyone know which one it is?
I remember it is a one line only that I think showed some basic info of the disk thus had to wait before it was ready...

Best regards

---

### Post by hwttdz on 2011-05-25
"eject -t" will close the drive, not supported on all drives. "eject -T" will change the state of the drive (open->closed, closed->open).  I guess there's still the issue of waiting until ready to read, but you should be able to do some parsing of /etc/mtab or mount to get that.

---

### Post by vascofg on 2011-05-25
I know that 'eject -t' loads the drive, but I'm asking for something that actually waits until the disk is ready to write to before continuing.
Like I said I know such program exists since I've used it before, but since have formatted so lost the script.

---

