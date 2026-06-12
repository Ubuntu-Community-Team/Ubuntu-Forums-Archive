---
title: "Wubi disk after reinstallation"
date: 2012-02-13
forum: General Help
---

### Post by phone199 on 2012-02-13
I have my Ubuntu reinstalled with Wubi, and before that I moved my home.disk (contains my videos, pictures, ect, created by sudo sh wubi-add-virtual-disk /home 15000) to a new directoy in Windows 7, so it doesn't destroyed. For now, the new Ubuntu System doesn't set the home.disk as home, so can I set home.disk as home folder of Ubuntu without overwritten the data on the home.disk? and how should I do?

---

### Post by bcbc on 2012-02-13
You could copy the home.disk back to the /host/ubuntu/disks/ directory.
Then edit the /etc/fstab, move your current home out of the way and then reboot.

```
gksu gedit /etc/fstab
```

Add a line for your separate home.disk (I assume it's ext3 if you used that script)
```
/host/ubuntu/disks/home.disk    /home    ext3    loop    0    0
```

Backup your current home and reboot (you can delete /homebackup later):
```
sudo mv /home /homebackup
sudo reboot
```

---

### Post by chies27 on 2012-02-15
Thank you very much good man, it really works!

---

