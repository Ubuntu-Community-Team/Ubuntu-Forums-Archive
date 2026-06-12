---
title: "No cd drive, want to reinstall"
date: 2009-07-16
forum: General Help
---

### Post by wildmonkeys77 on 2009-07-16
Hey thanks in advance for your help

I just inherited a dell "n series", a very small laptop with no cd drive and ubuntu pre-installed.

My hard drive is 100% full and rather than figure out which files are neccessary and which ones are unneccessary, I want to just clear everything out, re image and re install ubuntu.

How can I do this without a cd drive?

---

### Post by TheSmokingGNU on 2009-07-16
er... got a flashdrive?

hoping you have a USB port. otherwise, wait for some linux gurus. there might be an in-system way, but I'm relatively new at this. sorry.

Good luck!

---

### Post by c0mput3r_n3rD on 2009-07-16
Flash drive would be the best way as the above poster suggested.

---

### Post by wildmonkeys77 on 2009-07-16
I do have a USB port...can you install it from that? I read some tutorials but they seemed to give patchy results to those who commented

---

### Post by zeronothing on 2009-07-16
Depending on which version you have, as long as its version 8.10 or 9.04 you can create a USB installer. In the two versions I mentioned above they have a feature called "USB Startup Disk Creator." its located at:

System -> Administrator -> USB Startup Disk Creator

First you will need a a 1gb usb stick and an .iso image of ubuntu. once you have those two things you can create the usb installer. open up the "USB startup Disk Creator" and click on the "Other" and select the .iso image of ubuntu that you downloaded. then with your usb stick inserted into the machine, click on "Make Startup Disk." After it gets done making the USB installer disk, you can then restart your machine and boot from USB. Also you may want to check to see if you PC can boot from USB. You can check for this in your PC's BIOS

---

### Post by zeronothing on 2009-07-16
you might want to check this documentation out.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by wildmonkeys77 on 2009-07-16
8.04 is what i have, and currently I'm on a trip and only have a 512MB flash drive :(

---

