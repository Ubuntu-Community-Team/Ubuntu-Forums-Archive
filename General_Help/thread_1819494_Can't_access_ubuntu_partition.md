---
title: "Can't access ubuntu partition"
date: 2011-08-06
forum: General Help
---

### Post by Vizuh on 2011-08-06
I already posted this but no-one gave me any decent replies. 

I have ALL of my holiday pictures saved there and that is the ONLY place where they are. The Ubuntu partition is corrupt and unaccesible. I NEED to get these pictures back, help.

---

### Post by Vizuh on 2011-08-06
Anyone?

---

### Post by lmarmisa on 2011-08-06
Open a terminal, type these commands and post the results:

```

sudo lshw -C storage -C disk
sudo fdisk -l
sudo parted -l
mount

```

---

