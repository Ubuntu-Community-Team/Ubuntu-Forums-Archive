---
title: "Extremely dark screen (almost black)"
date: 2012-07-01
forum: General Help
---

### Post by jimmydene84 on 2012-07-01
my laptop never liked previous versions of ubuntu. its a hp pavillion g7, never could connect to wifi on previous versions so i gave up. just recently put 12.04 in a disk and it all worked fine, even can connect to wifi now!! but after about 5 minutes of messing around my screen is so dark i can not use it, Its almost black...any tips hepl suggestions would be GREATLY appreciated


when i close the lid and open it back up it flashes back on, then goes to black after displaying this message...."no irq handler for vector (irq -1)"

im sure thats telling me whats wrong but i dont know what it means or how to fix it

---

### Post by mcclunyboy on 2012-07-01
this maybe something similar to something i experienced a few years back...basically you have a device which is enabled but the driver wasn't working properly...i assumed it was an interrupt of some kind - 

if you can try  the following to see if anything is causing an interrupt
```
 cat /proc/interrupts
```In one of the columns it may state something about IRQ - is anything listed?

Of course I maybe barking up the wrong tree and someone more experienced needs to chip in...

---

### Post by jimmydene84 on 2012-07-01
alright, read some things and held "shift" and got into "grub"? and selected the nomedeset option and no more black screen....but its still running off the disk....i want to install it and dual boot but everytime i select install ubuntu 12.04 it never finishes, it starts then tells me to eject the disk and hit enter and when i do it boots into windows??

---

### Post by mcclunyboy on 2012-07-01
when you put the install disk in?

does it look to have installed but when it compeltes and asks you to remove the disk does it reboot and boot windows (once open in windows has ur partitions been created correctly).

---

