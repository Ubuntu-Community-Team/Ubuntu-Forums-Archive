---
title: "testing the recorded .iso CD"
date: 2006-04-24
forum: General Help
---

### Post by TitusDalwards on 2006-04-24
i have just downloaded ubuntu Breezy and i record .iso files to cd but i want to learn that everything well before  installing. is there any way to learn this?thanks lot

---

### Post by TitusDalwards on 2006-04-25
ok i ave found the solution yet:
you can control the recorded CD and iso  file bye this command:
```
dd  if=/dev/cdrom  of=/dev/null  bs=1M
```

---

### Post by iball on 2006-04-25
Try:
```
md5sum /dev/cdrom
```
And compare with the md5sum of the downloaded ISO file.

Also, open the CD in the file manager, and make sure that the files are there.  You should have several directories and maybe some other files on the CD.

This always seems to work for me
--Ian

---

