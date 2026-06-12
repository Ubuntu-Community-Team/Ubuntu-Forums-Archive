---
title: "Stuck in Boot Screen"
date: 2009-10-01
forum: General Help
---

### Post by Anxious on 2009-10-01
Hi,

I installed Ubuntu in windows, and when i try to start ubuntu im stuck at the first 5% of the loading bar and even after waiting patiently ( or rather sitting in front of my tv ) it doesnt move an inch. 

I dont know if its connected but when i tried to install it via booting from the ubuntu cd the installation didnt want to start.
( after hittin enter on "install.." i just got a flashing underline like if it was waiting for an input ( it wasnt ))

Im using the msi cx 700 notebook with the pentium t4200

[http://uploaded.to/file/ssn7ha](http://uploaded.to/file/ssn7ha)

is the cpu z report.

hope somebody can help me.

--

dont know if it helps, but if i try to boot from the ubuntu cd in "try out" mode i get something simmilar like when i try to install it, a flashing underline and nothing happens.

---

### Post by NightwishFan on 2009-10-01
If you have it installed in Windows using WUBI, but it will not boot up, try this:

After selecting Ubuntu, it will say press esc to enter menu at the top. Do so, and the first line will say Ubuntu (and kernel version).

Push "e" to go to a new menu, highlight the line called kernel then push "e" again.

Then at the end of the line add this option:
```
acpi=off
```

Push enter, and then "b"

If it boots, then I can tell you how to make the change permanent, if not, then we shall see.

---

### Post by Anxious on 2009-10-01
thanks, it did work ! and now it does install the basic system :),

how to make it permanent ? and why does the power management interfer with my booting?

---

### Post by NightwishFan on 2009-10-01
As for why, at the moment, I am not sure. Though I could figure it out likely, I have to go soon.

To make it permanent:

Press alt+f2, and in the box that comes up type this:
```
gksudo gedit /boot/grub/menu.lst
```

In the text editor, scroll down until you find a section that looks like this:
```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot
```

On the line called 'kernel' in both Ubuntu and Recovery Mode, add the option 'acpi=off' right at the end, so it will be like: quiet splash acpi=off

Safe the file, you are good to go!

ONLY ADD acpi=off DO NOT EDIT ANYTHING ELSE

Good luck, I have got to sign off. :KS

---

