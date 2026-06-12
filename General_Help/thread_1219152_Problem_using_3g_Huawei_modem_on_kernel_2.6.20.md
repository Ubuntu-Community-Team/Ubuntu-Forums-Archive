---
title: "Problem using 3g Huawei modem on kernel 2.6.20"
date: 2009-07-21
forum: General Help
---

### Post by Sidewinder1 on 2009-07-21
With all due respect, 2.6.20 is a rather old kernel, 2007 I believe. Unless you have a very specific reason for using it, usually the newer kernels have more comprehensive support for a wider variety of hardware configurations. Just my $.02 and you're perfectly welcome to tell me that my advice is worth exactly what I'm charging for it... :-)
HTH,
Side

---

### Post by Sidewinder1 on 2009-07-22
No problem; I just wish I could've been of more help.. :-(

---

### Post by NoReflex on 2009-07-22
Hello!

Please plug in the modem and then check the output of : **tail /var/log/messages**.
It should tell you the modem was connected and more important it will tell you which driver it chose for the device (for my Huawei E220 the **option** driver works very well).

Good luck!
NoReflex

---

### Post by benj1 on 2009-07-22
the 2.6 kernel doesn't support 3g modems the newer 2.8? kernel does, im using an option 3g modem, i got a driver from pharscape.org, i think they have one for huawei modems aswell, have a look there.

---

### Post by benj1 on 2009-07-22
> **paddyoquinn said:**
> ok lol firstly the current kernel version for linux is 2.6.30 you probably mean 2.6.8 and no its natively supported in the kernel after version 2.6.19 so with my 2.6.20 kernel is should work with my current kernel, but i fear that the kernel has been stripped of the driver that allows the Modem to be read as a modem rather than a CD device or mass storage device, ttyUSB0 had to be added by me manually because it didnt show up in the /dev/ folder which is should have done on conncetion, but still nadda
Thank you for your input however it ads to my tought process on solveing my problem :)
Regards
Patrick
hmm by bad i thought they had moved up a version in jaunty and that most 3g modems were supported(should have checked).
my kernel is 2.6.24(hardy) and mine doesn't seem to be detected by network manager although it could be the other drivers interfering don't know.
im glad you appreciated my (completely wrong) input :)

---

### Post by NoReflex on 2009-07-22
paddyoquinn,

the command is tail **/**var/log/messages.
It should exist. If you issue the command without **/** it would search for var/log/messages in the current directory.
You could also plug in the modem, reboot with the modem plugged in and you should see how it detected it with dmesg ...

Hope this helps you!

Best wishes,
NoReflex

---

