---
title: "Bad SD card data recovery"
date: 2012-03-20
forum: General Help
---

### Post by gregor171 on 2012-03-20
I have an ScanDisk 16GB SD card that was put into Windows XP machine and after that it lost partition and data. 

Disk utilita shows: /dev/mmcblk0 32MB (was 16GB)

Any ideas how to rescue disc and data as well?

---

### Post by winh8r on 2012-03-20
You should be able to recover the data using testdisk/photorec.

You can install testdisk by opening a terminal and entering:
```

sudo apt-get install testdisk
```

There is a step by step guide to using testdisk here:

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Read the instructions carefully before attempting to recover anything, and if you have any questions, just ask them before you try any recovery.

Hope this helps you.

---

### Post by dcstar on 2012-03-20
> **winh8r said:**
> You should be able to recover the data using testdisk/photorec.
.........

Unless it is dead, which happens all the time to these things because people don't realise that they all will die eventually - especially when used in major multiple-write environments like computers.

---

### Post by winh8r on 2012-03-20
> **dcstar said:**
> Unless it is dead, which happens all the time to these things because people don't realise that they all will die eventually - especially when used in major multiple-write environments like computers.
 Yes , unless it is dead. But I tend to think like a paramedic where these things are concerned. Don't give up until you are certain that life is extinct.

Always worth a try.

---

### Post by gregor171 on 2012-03-20
Card is new and worked well untill entered into old Win XP machime!

Basically I tried many things as well testdisk and there are 2 tipical errors:

"unknown partition table"
"artition sector doesn't have the endmark 0xAA55" testdisk that aslo see only 32MB?!?

Does anyone knows what partition type is used in SDHC cards?

Thx!

---

### Post by winh8r on 2012-03-20
Did you run photorec on it to try to recover the data?

---

### Post by gregor171 on 2012-03-20
No! cause it looks like there could be something wrong with disk geometry?

I think photorec can't be used if I don't see the correct partition: 16GB to 32MB.

---

