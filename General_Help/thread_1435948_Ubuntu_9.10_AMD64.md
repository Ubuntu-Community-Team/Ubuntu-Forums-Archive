---
title: "Ubuntu 9.10 AMD64"
date: 2010-03-22
forum: General Help
---

### Post by esky64 on 2010-03-22
Hi I have read that Ubuntu 9.10 64 Bit has a problem. but the thread closed My Ubuntu 9.1064Bit keeps on freezing IO read that I was a kernel problem has this been fixed.  doing a test at the moment it may look like a firefox problem. Is there a other good browser that I can use till it is fixed.I can leave ubuntu running with no program working and see fit it freezes I will keep you posted 
Chris

---

### Post by prodigy_ on 2010-03-22
Which kernel version do you use? Use ```
uname -r
``` command if you're unsure.

---

### Post by esky64 on 2010-03-22
> **prodigy_ said:**
> Which kernel version do you use? Use ```
uname -r
``` command if you're unsure.
Thanks you very much for the command.
2.6.31.20-generic

---

### Post by prodigy_ on 2010-03-22
> **esky64 said:**
> Thanks you very much for the command.
2.6.31.20-generic
I've found 2.6.31-20 to be problematic and suggest you to revert to the previous version. At least give it a try:
```
sudo apt-get install linux-image-2.6.31-19-generic linux-headers-2.6.31-19-generic linux-headers-generic
```
Then reboot, choose 2.6.31-19 from Grub menu and see if that helps.

---

### Post by esky64 on 2010-03-24
Thanks prodigy
looks like stability has returned to my machine.
My question mow, How to I make 2.6.31.19 my default in grub
Update 
No System just froz again I think it might be a sleep mode problem.
Can I from ubuntu find out what my motherboard details are BIOS etc maybe even the way western digital power down there green sata HDD's?

---

