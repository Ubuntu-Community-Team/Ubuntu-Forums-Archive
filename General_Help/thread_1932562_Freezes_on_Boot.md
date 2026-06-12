---
title: "Freezes on Boot"
date: 2012-02-27
forum: General Help
---

### Post by watupgroupie on 2012-02-27
Hi, I recently built a new PC and was wanting to boot Ubuntu or any linux distro on it, but it keeps freezing during the initial boot process. This is a picture of exactly where it freezes: [http://i179.photobucket.com/albums/w289/watupgroupie/IMG_20120226_201924.jpg](http://i179.photobucket.com/albums/w289/watupgroupie/IMG_20120226_201924.jpg)

The specs are: 
Intel Core i5 2500k
Asus P8Z68-V LE motherboard
Nvidia GTX 570
8.00 GB Dual-Channel DDR3 @ 686MHz
Seagate 500GB HDD

I've read a little bit on the motherboard and it looks like other people have successfully booted up on it before. I already posted on the Installation sub forum but received no responses. Any ideas?

---

### Post by watupgroupie on 2012-02-27
Bump. Anyone? Is there something I'm missing with the hardware possibly?

---

### Post by thinkdez on 2012-02-27
Looks like you are freezing while it loads information about your disk.  Have you tried to remove the Hard drive and boot with the LiveCD?  Does that work?  If so your drive or disk controller may be the problem.

---

### Post by rollinsmoke on 2012-02-27
bit of a shot in the dark but i had a simaler problem it turned out to be a bad sata cable that came with my board. intel acttualy sent me a new one i had to call them thinking something was screwie with my board

---

### Post by watupgroupie on 2012-02-28
I removed the HDD from the equation and it still froze in the exact same place. I'm doubting it's any kind of sata cable issue because I disconnected all of them just to be sure and had the same result. So frustrating! 

I tried launching in UEFI mode on the USB stick and it did bring up the menu to install ubuntu or try it out first, but after I clicked either of them it went to a black screen and never made it past it.

---

### Post by watupgroupie on 2012-02-28
Bump. Anymore ideas guys?

---

### Post by rollinsmoke on 2012-02-29
have you tried booting your media on another computer mabye your disc/usb stick are faulty ive dont that burn it too fast and have random issuses also if your bios reconizes your drives i dont see why ubuntu wouldn't btw

---

### Post by dFlyer on 2012-02-29
Before you burned the iso to the usb did you check the md5sum? Did you check the burned usb disk from the ubuntu boot memu? You may want to do all this before you go any further.

---

