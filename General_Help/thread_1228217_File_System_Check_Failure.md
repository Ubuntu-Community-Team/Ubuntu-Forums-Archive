---
title: "File System Check Failure"
date: 2009-07-31
forum: General Help
---

### Post by deadmanmss on 2009-07-31
im having problems logging into my ubuntu

everytime i try to log in it starts to do the file system check and then it fails and i cannot log in

here is what it says

> *An automatic file system check (fsck) of the root filesystem failed.
a manual fsck must be performed, then the system restarted.
the fsck should be performed in maintenace mode with the root filesystem mounted in read-only mode
* the root filesystem is currently mounted in read-only mode.
a maintenace shell will now be started.
after performing system maintenace, press CONTROL-D
to terminate the maintenance and restart the system
bash: no job control in this shell




how do i performe the manual fsck?
or does anyone else have any idea on how to fix this

ive also taken a picture for more detail

[http://img352.imageshack.us/img352/3274/image287.jpg](http://img352.imageshack.us/img352/3274/image287.jpg)

---

### Post by michy99 on 2009-07-31
When you get to the point in the screenshot, enter```
fsck /dev/sda5
```

---

### Post by ajgreeny on 2009-07-31
If that does not work you can also do it from a live CD.  Boot to ubuntu live CD, open a terminal and then ```
sudo fsck /dev/sda5
```

---

### Post by deadmanmss on 2009-07-31
thanks ill give it a go tomorrow

---

