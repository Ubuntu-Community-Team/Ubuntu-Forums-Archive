---
title: "Need help removing folders"
date: 2010-11-24
forum: General Help
---

### Post by joelw135 on 2010-11-24
I have a few folders I need to remove and when I right click delete or move to trash not available. I guess I don't have permission. I am the sole user of this machine and the Admin. How do I remove these folders. The folders were part of ClamAV which has been removed. They show up as a virus in my Avast Anti Virus.

Never mind found the answer!

---

### Post by Hippytaff on 2010-11-24
If you need to be root to delete them open a terminal (CTRL+ALT+T) and try
```

sudo rm /path/to/fileneame

```
eg
```

sudo rm /CLamAV/somename.txt

```

---

### Post by joelw135 on 2010-11-24
> **Hippytaff said:**
> If you need to be root to delete them open a terminal (CTRL+ALT+T) and try
```

sudo rm /path/to/fileneame

```
eg
```

sudo rm /CLamAV/somename.txt

```

Thanks, found the answer Gksudo Nautilus

---

### Post by Hippytaff on 2010-11-24
Thats the other way :-) I'm a bit of a command line junkie :-)

---

