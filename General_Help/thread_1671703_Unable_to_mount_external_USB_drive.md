---
title: "Unable to mount external USB drive"
date: 2011-01-20
forum: General Help
---

### Post by rmcellig on 2011-01-20
I have an external drive plugged into my laptop but am unable to mount it. I can see it in Gparted but when I right mouse click on the drive, there is no option to mount.

---

### Post by Smart Viking on 2011-01-20
The drive is sda1, right? If so the following should help you, if it doesn't report back the output.

```
sudo mkdir /media/mount
sudo mount /dev/sda1 /media/mount
```

---

### Post by rmcellig on 2011-01-20
Thanks. That worked. Any idea why it wouldn't mount in the first place?

---

### Post by rmcellig on 2011-01-20
Thanks. That worked. Any idea why it wouldn't mount in the first place?

---

