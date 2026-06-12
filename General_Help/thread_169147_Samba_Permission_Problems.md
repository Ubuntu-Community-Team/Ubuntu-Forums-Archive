---
title: "Samba Permission Problems"
date: 2006-05-02
forum: General Help
---

### Post by leviathan660 on 2006-05-02
I'm attempting to set up a Network drive from my PC's, and I was finally able to mount my sda5 drive (Fat32) onto Windows, but I am not able to Write to the Drive. I checked out the chmod, and its at 755. I when I try and change it to 0777, it just switches back to 755, can anyone help me make this network drive?

---

### Post by Jason_25 on 2006-05-02
This is because ubuntu's default fat32 umask is 022.

Append these lines to the options section of the fstab for your partition.
```

fmask=0177,dmask=0077,uid=1000

```
This will mount the drive with better security than umask=000.  But you can always try that if this doesn't work.

---

### Post by leviathan660 on 2006-05-02
I tried putting both those lines in my fstab, but unfortunatly those did not work, any more ideas?
--Edit--
Great, now Ubuntu never asks me for my sudo password whenever I'm doing anything

---

### Post by Jason_25 on 2006-05-02
I'm afraid you might have added those options to your root partition.  If so, you  need to remove the options and remount the drive.  Those options are only for fat32 drives.

---

