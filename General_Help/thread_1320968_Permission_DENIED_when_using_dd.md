---
title: "Permission DENIED when using dd?"
date: 2009-11-09
forum: General Help
---

### Post by clevertomato on 2009-11-09
I'm trying to use dd to install an embedded image of FreeNAS to a CompactFlash card on a PC other than the target PC per instructions found at: [http://m0n0.ch/wall/installation_generic.php](http://m0n0.ch/wall/installation_generic.php)

It's seems pretty simple, but no matter what I try, I get "Permission Denied" when running the command: gunzip -c file.img | dd of=/dev/sdb bs=16k

I've tried it while the CF is mounted AND unmounted. I've tried sdb and sdb1. I've tried using chown -R myuser:myuser.

Of course I've tried using "sudo" at the beginning of the command. I don't know why it's not allowing me access. I've even tried mounting it and pointing the dd command to the /media/CompactFlash directory even though I knew that isn't how it's supposed to work.

What could be the problem?

---

### Post by sisco311 on 2009-11-09
try:
```
gunzip -c file.img | sudo dd of=/dev/sdb bs=16k
```

BE CAREFUL!!!

or
```
sudo -i
```
to simulate initial root login.

press Ctrl+d or type *exit* to log out from the root shell.

---

### Post by clevertomato on 2009-11-09
THANKS! That worked ("sudo" after pipe before "dd"). I never would've thought to put "sudo" immediately before the "dd" after the pipe. I'm learning a lot as a relatively new GNU/Linux user, but still don't have a lot of experience.

I also have been wondering how to login as initial root under Ubuntu. Bonus answer for me. Thanks again.

---

