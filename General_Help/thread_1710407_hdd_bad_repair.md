---
title: "hdd bad repair"
date: 2011-03-19
forum: General Help
---

### Post by noxified on 2011-03-19
How do i repair bad sectors using ubuntu?(no other live cd etc)
sudo badblocks -sv /dev/sdb
Checking blocks 0 to 80043263
Checking for bad blocks (read-only test): 48846400done, 13:39 elapsed
48846420done, 14:06 elapsed
48846421done, 14:16 elapsed
48846422done, 14:25 elapsed
48846423done, 14:34 elapsed
__________________done          
How do i isolate them so i can use hdd without fear that i could lose any data?(not necesarily to install any os on it.Only for random data.
Can i install ubuntu on that hdd,without fearing that next time when i`ll open computer my pc will crash?
I have another hdd ,but i would like to use that hdd too.
It`s a 80 gb hdd,maxtor,sata.

---

### Post by dcstar on 2011-03-19
> **noxified said:**
> How do i repair bad sectors using ubuntu?(no other live cd etc)
.......     
How do i isolate them so i can use hdd without fear that i could lose any data?(not necesarily to install any os on it.Only for random data.
Can i install ubuntu on that hdd,without fearing that next time when i`ll open computer my pc will crash?
I have another hdd ,but i would like to use that hdd too.
It`s a 80 gb hdd,maxtor,sata.

```
sudo e2fsck -c
```

If a disk has bad blocks now then it will get worse, throw it out.

---

### Post by noxified on 2011-03-19
and what`s the syntax that i tell wich hdd to repair?
I already have ubuntu installed(and running) to another hdd.:D
I don`t have cd/dvd rom to start live.And from stick,it`s takes ages beacuse i don`t have usb 2.0.So i rather use smth from installed ubuntu.

---

### Post by noxified on 2011-03-20
anyone?:(

---

### Post by WorMzy on 2011-03-20
You cannot repair bad sectors. HDDs ship with a special reserved area which is used in place of bad sectors. Once this area has been used up, the HDD probably isn't going to last much longer anyway. Back up as much data as you can, then replace it.

---

### Post by noxified on 2011-03-20
ok,not necesarily to repair.Just to isolate them...

---

### Post by noxified on 2011-03-20
c`mon ppl.:D

---

