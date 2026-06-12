---
title: "ZTE blade isn't recognized"
date: 2011-07-08
forum: General Help
---

### Post by Yours3lf22 on 2011-07-08
Hi,

I have a ZTE Blade with Android 2.2. I tried to connect it to my pc via USB, however after I touch the "mount" button on the phone it seems to connect, but it is not recognized by my pc. I have kubuntu 11.04, freshly installed with latest updates, and ati driver. (The same thing happens with ubuntu 11.04)
The phone is GEN2 without any modification or rooting, when I tried it on a windows  pc it did connect without any problems.

Best regards,
Yours3!f

---

### Post by W3ird_N3rd on 2011-10-08
I know it's an old post, but people may find this thread through a search engine (like I did).

The solution is not easy to be found: [http://androsapiens.com/viewblog/viewpost/52](http://androsapiens.com/viewblog/viewpost/52)

In short, open /lib/udev/rules.d/40-usb_modeswitch.rules and remove or outcomment (with a #) the following line:

ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0083", RUN+="usb_modeswitch '%b/%k'"

And restart udev (or just reboot your computer). Presto!

---

### Post by Yours3lf22 on 2011-10-08
yes its an old post of mine. While this might solve it, I've found a forced solution: remove usb-modeswitch :)
anyways thanks for the reply

---

