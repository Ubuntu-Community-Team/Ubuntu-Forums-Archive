---
title: "DIff between /media/cdrom and /media/cdrom0 ?"
date: 2010-02-27
forum: General Help
---

### Post by pstein on 2010-02-27
In my /media directory I found two cdrom entries:
 
/media/cdrom
 
and 
 
/media/cdrom0
 
What is the difference?
 
Can I hide/disable/omit one of them?
 
if yes: how?
 
Peter

---

### Post by pstein on 2010-06-16
...no answer?

---

### Post by 98cwitr on 2010-06-16
these are directories and cdrom0 gets created when it has a problem unmounting /media/cdrom (to my knowledge). You can get rid of /media/cdrom0 and then remount you opt. drive to /media/cdrom

```

sudo umount /media/cdrom0
sudo rm -rf /media/cdrom0
sudo mount /dev/cdrom /media/cdrom

```

Where /dev/cdrom is the cdrom drive. 

That should do it.

---

