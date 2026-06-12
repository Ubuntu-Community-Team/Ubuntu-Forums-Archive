---
title: "Problems with upgrading to 11.10"
date: 2011-11-01
forum: General Help
---

### Post by jjweber4540 on 2011-11-01
The other night I was upgrading from 11.04 to 11.10. While i was installing my laptop was incidentally unplugged and shut off. When I start the computer now it says, "Waiting for network configuration." After that it says, "Booting system without full network configuration..." and then freezes. I don't know what to do to fix this. I am hoping you guys can help! I do have the USB drive i installed 11.04 with. I am okay with reinstalling if that is the only option.  Thank you in advance!

---

### Post by choochoousmc on 2011-11-01
not being a professional here.
It sounds like you will have to boot from the USB.
Then possibly reformat the hard drive, hope you backed stuff up.
Almost anytime you lose power during an install, it screws up the drive.
If you can boot from usb, see if you can read the main hard drive.
If so save what you can.
Try a reinstallation of 11.04, then do your upgrade

---

### Post by jjweber4540 on 2011-11-02
can I change the boot order before it freezes?

---

### Post by Mark Phelps on 2011-11-02
> **jjweber4540 said:**
> can I change the boot order before it freezes?

Possibly -- if you know the key combination to press to get into the BIOS settings.

---

### Post by jjweber4540 on 2011-11-02
no, do you know?

---

### Post by agillator on 2011-11-02
First, what medium were you using to install 11.10? You can probably just boot from that medium and redo the install, depending upon several things, for example were you replacing the previous system, etc. But that is the first thing to try. If you need to change the boot order, reboot your machine. At the very beginning - you may have to look quickly - it should tell you something like 'to enter bios press xxx' or some sort of message like that. If it goes by too fast you might try pressing the pause key while it is displaying. Which key your computer uses I don't know but the common ones seem to be the delete key (del), F1 or F2 - I've seen all of them used at one time or another. Anyway, in the bios there will be an option or set of options that will change the boot order. If you are still having problems then, assuming you installation medium is the usual live CD or live USB, go ahead and completely boot from it. Then you can prowl around with gparted to check the partitioning of your disk to see if that is the problem and hopefully fix whatever is wrong, then install from there.

---

