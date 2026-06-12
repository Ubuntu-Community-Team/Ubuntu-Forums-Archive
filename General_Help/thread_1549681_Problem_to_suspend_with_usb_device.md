---
title: "Problem to suspend with usb device"
date: 2010-08-10
forum: General Help
---

### Post by alda2 on 2010-08-10
I have ubuntu 10.04 installed. I have a problem when my usb IR receiver is connected, than suspend mode isn't working. System will jump into black screen and that's all. Only hard reset works. I tested this problem also on ubuntu 9.04 and situation is the same.
Is there any way how to force suspend mode without "looking" on this device ? 

Thank you for each information which will help me solve this problem. 
Do you need any log file to trace reason of this problem ?

Thanks

Alda

---

### Post by alda2 on 2010-08-10
I sending some log file, maybe will help ....

---

### Post by alda2 on 2010-08-10
again as zip files

I also tested directly from terminal send this :

sudo /etc/acpi/sleep.sh force

with this result :
trny@XBMCLive:~$ sudo /etc/acpi/sleep.sh force
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory

and the same result - black screen with blinking cursor upper left corner.

---

