---
title: "mount ext3 in ubuntu live"
date: 2006-01-31
forum: General Help
---

### Post by maxdevis on 2006-01-31
how can i mount my linux-partition when i'm in the ubuntu-live cd?

---

### Post by linuxden on 2006-01-31
[QUOTE=maxdevis]how can i mount my linux-partition when i'm in the ubuntu-live cd?[/QUOTE]

Now IMO only this is the way i would do it...

I would open up a terminal and use this command:

```
 sudo mount /dev/hd* /mnt 
```

where hd* is the number of the partition/drive you want to mount.

To access the files you open up a nautilus window and browse to /mnt

---

### Post by maxdevis on 2006-01-31
thanks
but it onlu worked with this
sudo mount -t ext3 /dev/......

---

### Post by linuxden on 2006-01-31
did it not work with the command i gave you??

strange!? did you substitute hd* for the appropriate drive/partition info??

---

