---
title: "One or more disks failing"
date: 2009-11-15
forum: General Help
---

### Post by trice95 on 2009-11-15
Sorry if a similar post was made couldn't find it...

I just installed ubuntu 9.10 on my dell inspiron 1525, as soon as I boot up it says one or more disks are failing. I opened it up and it says my ATA SAMSUNG HM250ji 'has many bad sectors'. Self test says failed. So I scrolled down and says current pending sector count , the id is 197 and assessment says warning. I have no idea what this means but the computer is almost brand new and is running smooth. Please help or at leat tell me whats this means thanks.

---

### Post by mikewhatever on 2009-11-15
There has been a lot of false positives with that program in Karmic. If the computer is new, I wouldn't worry, and tell it to ignore the drive.
Here is some info on reallocated sectors from Wikipedia:

> Count of reallocated sectors. When the hard drive finds a read/write/verification error, it marks this sector as "reallocated" and transfers data to a special reserved area (spare area). This process is also known as remapping, and "reallocated" sectors are called remaps. This is why, on modern hard disks, "bad blocks" cannot be found while testing the surface – all bad blocks are hidden in reallocated sectors. However, as the number of reallocated sectors increases, the read/write speed tends to decrease. The raw value normally represents a count of the number of bad sectors that have been found and remapped. Thus, the higher the attribute value, the more sectors the drive has had to reallocate.


---

