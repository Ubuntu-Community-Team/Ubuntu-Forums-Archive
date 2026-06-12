---
title: "Several GRUB error messages on startup"
date: 2011-05-01
forum: General Help
---

### Post by hleinone on 2011-05-01
I just installed Natty on my laptop. It has SSD drive, so to align the file system to the physical block size properly I created the partitions manually. After the installation it only boots to the GRUB recovery console, so I tried re-installing GRUB from Live CD by: 
```
sudo mount /dev/sda1 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
```It now boots to the system but always shows the following error messages instead of the GRUB menu on every boot:
```
error: file not found. 
error: file not found. 
error: no suitable mode found. 
error: no video mode activated. 
error: file not found. 
error: file not found.
```I suspect that I've missed out something during the installation, since SSD drives seem to need some more attention. It'd be great if someone could point out what it was.

---

### Post by docksteaderluke on 2011-05-13
Try the following:


```
sudo update-grub
```

---

### Post by hleinone on 2011-05-13
Yes, that was the correct solution.

---

