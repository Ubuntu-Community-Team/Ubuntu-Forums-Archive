---
title: "disc checks"
date: 2012-08-15
forum: General Help
---

### Post by sanderella on 2012-08-15
In previous releases of Ubuntu, I used to get an automatic disc check running every 30 times I logged into Ubuntu. This isn't happening now. Can anyone tell me why, please.

---

### Post by cottfcfan on 2012-08-15
This isn't happening for me either, but you can run:
```
sudo touch /forcefsck
```
and reboot, & a file system check will run.

---

### Post by sanderella on 2012-08-15
Thank you cottfcfan! Will try this. :)

---

### Post by sanderella on 2012-08-15
It worked. :KS for you, sweetie.

---

### Post by ajgreeny on 2012-08-15
You could also set your own required check interval using tune2fs with command ```
sudo tune2fs -c 30 /dev/sdx#
```I have mine set for every 70 mounts and have done for many years now without a problem.

I have no idea why the regular check has been removed from the system; I have no doubt someone else will know why.

---

