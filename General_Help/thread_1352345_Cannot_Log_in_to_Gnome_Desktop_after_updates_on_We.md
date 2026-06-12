---
title: "Cannot Log in to Gnome Desktop after updates on Wednesday"
date: 2009-12-11
forum: General Help
---

### Post by annabels on 2009-12-11
Hi,
 
I have had a standard Ubuntu 9.10 installation on my laptop for about 6 weeks.
On Wednesday evening I ran the Update Manager (and I think was asked to restart the computer).
 
Since then I cannot log in normal way. I choose a grub option in the normal way the screen goes black with white logo as normal... . But then screen starts pulsing between the black of _off_ and, the black of _on but displaying all black with a timer symbol in the middle_. If I move the mouse during this I will see a flash of white starting in the middle and moving wherever. But it always starts back in the middle.
 
This happens with all 3 kernels installed 2.6.31-14-generic, 2.6.31-15-generic, 2.6.31-16-generic.
 
Luckily I can get to recovery mode - black screen white text with prompt and log in and access all files (but not the internet).
 
I have tried various solutions suggested to people with similar problems like adding **vga=773** to the boot options (didn't work).
 
And when I enter at prompt:
```
startx
```
I get the following error message:
```
Error setting MTRR (base=0xa0000000 size=0x04000000 type=1) Invalid Argument(22)
```
 
I also tried to edit the **xorg.conf** file but *could not find it in the /etc/X11 directory*. Is this the problem????

---

