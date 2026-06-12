---
title: "having trouble setting a grub boot splash..."
date: 2009-09-01
forum: General Help
---

### Post by jason.b.c on 2009-09-01
how do i get my (x)ubuntu to tell me what partition it is installed in...?


i'm pulling my hair out...:D because i still can't seem to my bootsplash to work...

thanks..

---

### Post by falconindy on 2009-09-01
I haven't used it myself, but you may want to try using usplash to manage your bootsplash.
```
sudo apt-get install usplash
```
You shouldn't need to specify the location of the boot partition.

---

### Post by jason.b.c on 2009-09-01
ok , but is there a terminal command to have the system tell me which partition it is in...?

---

### Post by falconindy on 2009-09-01
Run `sudo gparted` and find the partition flagged as boot. GRUB itself is installed to the MBR (the first 512 bytes of the boot drive), which is out of your immediate reach.

---

### Post by jason.b.c on 2009-09-01
just as a note , the usplash thing caused my system to crash out just now..

---

