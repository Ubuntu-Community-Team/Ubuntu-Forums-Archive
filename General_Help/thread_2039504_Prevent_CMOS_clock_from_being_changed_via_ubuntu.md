---
title: "Prevent CMOS clock from being changed via ubuntu"
date: 2012-08-09
forum: General Help
---

### Post by adromidon on 2012-08-09
I have Ubuntu 12.04 installed in a dual boot setup with windows 7, every time I load Ubuntu it changes the system (CMOS) clock to the UTC time zone, changing the time zone in Ubuntu seems to be superficial as it only alters the UTC time when displaying it but changes the core clock.

This would not be an issue if Ubuntu was the only OS i had but since i use Windows also, booting into windows after having Ubuntu loaded causes the Windows clock to become set to the CMOS clock meaning it will say 5am when its actually 1am.

In Fedora and other distros there is a way to prevent the kernel from changing the internal CMOS clock, how would one do this on Ubuntu?


I apologize if that sounds confusing look at the flow chart below for the issue in a graphical representation (sort of)

Ubuntu sets internal clock ---> reboot into windows ---> Windows detects wrong time due to Ubuntu resting the internal clock ----> must manually re-adjust the windows clock to correct the time.



What should happen 

Ubuntu reads the internal clock adjusts time to proper zone ----> Reboot into windows -----> time remains set for the correct time zone -----> Ubuntu did not alter the internal time

---

### Post by hansum_rahul on 2012-08-09
Probably you need to change your time zone.

Do a > tzselect and a > hwclock --systohc

---

### Post by QIII on 2012-08-09
Using gedit as an example --

```
gksudo gedit /etc/default/rcS
```Modify the line that says```
 UTC=yes
```and change it to ```
 UTC=no
```Save and reboot.

You may have to reset the Windows clock once then next time you boot to it.

---

### Post by wheeze on 2012-08-09
Check the file **/etc/default/rcS**

There should be a line in there that says **utc=no**

If it says **yes**, change it.

Also check the file **/etc/adjtime**. Not sure if it's there in Ubuntu, it is in Debian.

Make sure the last line says LOCAL, not UTC

---

### Post by Cheesemill on 2012-08-09
Another solution is to tell Windows to use UTC time as well, it can be done with a quick registry edit.
Just google 'windows utc' for details.

---

### Post by adromidon on 2012-08-09
> **Cheesemill said:**
> Another solution is to tell Windows to use UTC time as well, it can be done with a quick registry edit.
Just google 'windows utc' for details.

Believe it or not I am more comfortable editing an Ubuntu configuration file then I am editing the windows registry due to the registry being so easy to mess up the system.

I will try the edit to the rc file thanks for the tips !

---

### Post by adromidon on 2012-08-09
> **QIII said:**
> Using gedit as an example --

```
gksudo gedit /etc/default/rcS
```Modify the line that says```
 UTC=yes
```and change it to ```
 UTC=no
```Save and reboot.

You may have to reset the Windows clock once then next time you boot to it.

Excellent I will try this thank you so much!

---

