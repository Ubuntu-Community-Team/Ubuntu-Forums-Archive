---
title: "Mounting VHDs"
date: 2009-10-01
forum: General Help
---

### Post by Emarian on 2009-10-01
I have a VHD that I mount on Windows 7 that contains all of my files (music, movies, games, etc). It's easier to organize my files this way.

However, on Ubuntu, I can't mount it. I'm interested in making it an accessible folder.

Is this possible?

---

### Post by Giblet5 on 2009-10-01
Try mounting it as a loopback device.

```
man mount
```

Also see ```
man fstab
``` cuz you probably want to mount it at boot time.

---

### Post by Emarian on 2009-10-01
My command is:

sudo mount /media/disk/Storage.vhd -o loop

However, this prompts an fstab issue. How would I add a loopback to fstab?

EDIT:
I suppose the more appropriate question is what filesystem type would I specify in fstab?

---

### Post by Emarian on 2009-10-14
Can anyone help me out? I'm completely lost.

---

