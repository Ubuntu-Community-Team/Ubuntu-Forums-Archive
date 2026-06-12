---
title: "Mount my windows driver"
date: 2009-08-10
forum: General Help
---

### Post by Lord foff on 2009-08-10
I was wondering if anyone knew a way for me to access my windows files from my ubuntu, i have my pc on dual boot and cannot mount the drive.

---

### Post by merlinus on 2009-08-10
How are you trying to access the windows partition?  It should show up in Places, but perhaps with a name like 250G disk.

---

### Post by Lord foff on 2009-08-10
If i go to places i can see the drive (ubuntu and windows are on seperate drives), but if i try to access the files it comes up with a box saying cannot mount volume :(

---

### Post by merlinus on 2009-08-10
Are you using wubi, or dual-boot partitions?

---

### Post by CTBuckweed on 2009-08-10
My installation of Hardy shows the Windows/DOS drives in Places > Removable Media. Each partition has the name of the Windows/DOS partition's LABEL.

---

### Post by Lord foff on 2009-08-10
Wubi

---

### Post by Lord foff on 2009-08-10
> **CTBuckweed said:**
> My installation of Hardy shows the Windows/DOS drives in Places > Removable Media. Each partition has the name of the Windows/DOS partition's LABEL.

Mine just says 200gb media

---

### Post by Lord foff on 2009-08-10
bump

---

### Post by michy99 on 2009-08-10
The Windows partition where you installed Wubi is available as /host within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media

---

### Post by Lord foff on 2009-08-10
'Nautilus cannot handle this kind of location'

---

### Post by michy99 on 2009-08-10
What do you get when you enter this in a terminal?```
ls -ld /host
ls -la /host
```

---

