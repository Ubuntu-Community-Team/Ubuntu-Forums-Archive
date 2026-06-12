---
title: "Help! ntfs-config is segfaulting"
date: 2010-03-27
forum: General Help
---

### Post by bergqvistjl on 2010-03-27
What it says on the tin really, increased the size of my main (ext4) partition, and now whenever i try to launch ntfs-config i get a segfault. Nothing else, just that. Could it be because i deleted some (what i thought was) redundant stuff in my fstab file? Ive tried removing and reinstalling ntfs-config, but it has no effect. Any ideas?

---

### Post by spiderbatdad on 2010-03-27
did you make a backup copy of fstab? What editor did you use to edit the file. Gedit as root will automatically backup the original for you...to a hidden file of the same name: fstab~
Also look for /etc/fstab.pre-ntfs-config...use your terminal not nautilus:
```
 ls -al /etc 
```

---

### Post by n0dix on 2010-03-27
If the above suggestion doesn't work, try doing 'ls -la' in the /etc/ directory and show the output.

---

### Post by bergqvistjl on 2010-03-28
ive got a copy of the pre-ntfs-config fstab. Shall i replace my current one with that one and see what happens?

---

### Post by n0dix on 2010-03-28
But make a backup first.

---

### Post by bergqvistjl on 2010-03-28
ok well i changed contents the fstab to what it was before altered it with ntfs-config, rebooted, did a 'Completely Remove' of ntfs-config, rebooted again, installed it and its still segfaulting immediatly.

---

