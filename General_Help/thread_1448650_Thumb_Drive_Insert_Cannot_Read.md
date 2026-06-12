---
title: "Thumb Drive Insert Cannot Read"
date: 2010-04-06
forum: General Help
---

### Post by JJJCR on 2010-04-06
hi experts, i inserted a thumbdrive on one of the usb slots on my laptop upon inserting it shows:
[sdb] Assuming drive cache: Write through
[977.113519] sd 5:0:0:0: [sdb] Assuming cache: Write through

how to read the contents of my thumbdrive?

Do i need to mount it first or what should be the procedure?

Thanks. Please help. :P

---

### Post by JJJCR on 2010-04-09
> **JJJCR said:**
> hi experts, i inserted a thumbdrive on one of the usb slots on my laptop upon inserting it shows:
[sdb] Assuming drive cache: Write through
[977.113519] sd 5:0:0:0: [sdb] Assuming cache: Write through

how to read the contents of my thumbdrive?

Do i need to mount it first or what should be the procedure?

Thanks. Please help. :P

Through googling..i found a way on how to do this..

1. execute  "fdisk -l" to check which device is my thumbdrive

2. then i created a folder and  mount it :
       mkdir /media/usbdisk 
    then:
      sudo mount /dev/sdb1  /media/usbdisk

Thanks. :)

---

