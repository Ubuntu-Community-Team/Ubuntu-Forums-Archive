---
title: "Anybody ever seen this error with a live CD?"
date: 2010-01-31
forum: General Help
---

### Post by cptrohn on 2010-01-31
```
EXT3-fs: sda1: counldn't mount because of unsupported optional features (240)
Request_module: runaway loop modprobe bin fmt -464c
```

this isn't really an Ubuntu issue though, I was trying to run backtrack4 but since it is based on Ubuntu 8.10 I thought maybe there was something in Ubuntu that could help.

---

### Post by Leppie on 2010-01-31
did you install ubuntu using the ext4 format?
ext4 uses advanced features ext3 cannot read, not sure hardy supports the ext4 format.
what is it that you wanted to use off the backtrack 4 dvd?

---

### Post by cptrohn on 2010-01-31
> **Leppie said:**
> did you install ubuntu using the ext4 format?
ext4 uses advanced features ext3 cannot read, not sure hardy supports the ext4 format.
what is it that you wanted to use off the backtrack 4 dvd?


Actually I was just wanting to check it out, mostly just curious and experimenting with different distros.

But since I was booting it from a live cd would the EXT4 filesystem really effect it?

---

### Post by t4thfavor on 2010-01-31
Is it booting on a machine that has an EXT4 FS on it? If so, it's probably just a failure to mount the drive on the machine. The boot process will probably continue after some timeout period.

---

