---
title: "unable to mount hdd in laptop ubuntu 8.10"
date: 2010-07-28
forum: General Help
---

### Post by electricwizard on 2010-07-28
yeah it gives me this error:

[[IMG]http://img709.imageshack.us/img709/9315/pantallazodp.png[/IMG]]("http://img709.imageshack.us/i/pantallazodp.png/")

thanks in advance

---

### Post by Vishnu V on 2010-07-28
I think this is due to the improper shutdown of windows. And if you want to mount it open a terminal (Application->Accessories->Terminal) and type
```

sudo su
mkdir /media/ntfs
sudo mount -t ntfs-3g /dev/sda1 /media/ntfs -o force

```now you can access it

---

### Post by oldfred on 2010-07-28
Force may work and you can use as a last resort. If you just need to mount it to recover data it is a way to get to it.

But if the NTFS is hibernating or if improperly shutdown you should restart windows. IF it needs to run chkdsk it can then repair the problem. A force mount and any writing may prevent it from recovering with chkdsk and whatever file is corrupt will not be repaired (if even possible).

---

