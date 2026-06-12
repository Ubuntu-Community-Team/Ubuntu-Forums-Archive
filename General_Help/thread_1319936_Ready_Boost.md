---
title: "Ready Boost"
date: 2009-11-08
forum: General Help
---

### Post by CaseSensative on 2009-11-08
My favourite flash drive Xporter XT flash drive is not ready boosting with ubuntu..or is there no ready boost with ubuntu 9.10?
[B]
[/B]

---

### Post by munky99999 on 2009-11-08
1) plug the drive in your usb connector;
2) if ubuntu automount the device (usually in /media/usbdisk), umount the device (ie., sudo umount /media/usbdisk);
3) sudo mkswap /dev/sda1 (assuming /dev/sda1 is the correct device for the connected usb device)
4) sudo swapon -p 32767 /dev/sda1

Verification: cat /proc/swaps


[SIZE="5"][COLOR="Red"]The reality though is...[/COLOR][/SIZE]

Sure wont be used 99% of the time. Currently on any of my machines. The highest im using is 0.4% of my swap space.

Unless for some reason you seriously are burning out hard drives and are disk thrashing. You really dont need this.

To check this for yourself. Goto the System Monitor in system-admistration. Then to resources tab. 


The reason microsoft has come out with this. Is because they seriously require you to dump loads of their operating system to the pagefile/swap. Which tends to slow your whole system down. Meaning readyboost is an improvement. 

Totally unnecessary for ubuntu.

---

### Post by CaseSensative on 2009-11-08
Thank you for your help. Ha I am so used to windows needing that extra umph, so i was worried when I could not find the options. Or that my usb was shot, once again thank you!

---

