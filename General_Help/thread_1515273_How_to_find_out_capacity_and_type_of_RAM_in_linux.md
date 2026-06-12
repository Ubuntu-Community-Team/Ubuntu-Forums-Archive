---
title: "How to find out capacity and type of RAM in linux"
date: 2010-06-22
forum: General Help
---

### Post by rado3105 on 2010-06-22
Hi, is there any command to find out capacity of RAM and frequency, or more?

---

### Post by marshmallow1304 on 2010-06-22
```
sudo lshw -C memory
```

There are also several GUI tools, such as [hardinfo]("apt://hardinfo") and [sysinfo]("apt://sysinfo").

---

### Post by 11hjpphty76lkjj on 2010-06-22
lshw is awesome.  I usually do something like:

```
sudo lshw > hardware.txt
```

then

```
gedit hardware.txt
```

It will give you a lot of info on the system--not just the ram.

---

### Post by karthick87 on 2010-06-22
There are different RAMs DDR,DDR1,DDR2,DDR3 etc etc..I want to identify the type of RAM i use,how it can be done...?How to identify..?

---

### Post by pricetech on 2010-06-22
Look in the BIOS for that information.

---

