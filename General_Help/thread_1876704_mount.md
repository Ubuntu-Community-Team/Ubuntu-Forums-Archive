---
title: "mount?"
date: 2011-11-06
forum: General Help
---

### Post by Matrix01 on 2011-11-06
In home folder, clicked 4.3GB file system, clicked open, but it did not.
what will 'mount' do?

---

### Post by bluexrider on 2011-11-06
Did you check Permissions for usage.

---

### Post by Matrix01 on 2011-11-06
how do u check permission?

> **bluexrider said:**
> Did you check Permissions for usage.

---

### Post by Mark Phelps on 2011-11-06
Open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out your drives and their partitions.  I suspect, given that this is so small, that is is a USB stick and was formatted (by default) with a Windows filesystem (FAT).

---

### Post by Matrix01 on 2011-11-06
this USB stick is formatted with FAT 32, and Unetbootin is downloaded in this.


> **Mark Phelps said:**
> Open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out your drives and their partitions.  I suspect, given that this is so small, that is is a USB stick and was formatted (by default) with a Windows filesystem (FAT).

---

### Post by raja.genupula on 2011-11-06
Hi.
have you tried mounting manually 

```
sudo mount /dev/sdb1 /mnt
```

---

### Post by Matrix01 on 2011-11-06
not yet.
well,
my 11.04 was not booting after update.
i installed 11.04 with unetbootin in a few weeks ago,
thinking about another application.
did u use GRUB, and installed buntu?

> **raja.genupula said:**
> Hi.
have you tried mounting manually 

```
sudo mount /dev/sdb1 /mnt
```

---

### Post by raja.genupula on 2011-11-06
you said 11.04 not booting..so please explain the things happening at booting. 

> thinking about another application.
did u use GRUB, and installed buntu?


and explain this man , i didnt get it.

---

### Post by Matrix01 on 2011-11-08
well,
Ubuntu logo is on monitor, and
five, i guess, dots under logo keep blinking forever

---

