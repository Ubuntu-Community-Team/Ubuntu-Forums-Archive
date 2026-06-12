---
title: "Can't get netbook to boot off USB"
date: 2010-11-22
forum: General Help
---

### Post by Scooter_X on 2010-11-22
I just bought an ASUS Eee PC 1001PXB and for the life of me I can't get it to boot off of my startup disk I just made with 10.04 for netbooks. Anyone know what I'm doing wrong? I went in and changed the order so that the 'removable device' was first, then the cd-rom (which isn't attached, I didn't get one) then the hard drive. The flash drive flashes a bit during startup like it's trying to read it, but then windows boots up.

](*,)

---

### Post by Bradj47 on 2010-11-22
I have the exact same problem with my netbook. I used unetbootin to create a supposedly bootable flash drive from an iso file and my ASUS eeePC netbook won't boot from it. It did this with both Arch Linux and multiple versions of Ubuntu Netbook Remix. The only OS that didn't do this was eeebuntu, which I really don't recommend btw. I ended up installing Ubuntu 10.04 using an external DVD drive.

---

### Post by Scooter_X on 2010-11-22
Ha. Shoulda' youtube'd it before I posted. I found something, I had to :

*hit f2 during bootup during startup to get to the bios settings.

* Under 'advanced' -> IDE configuration I changed my SATA from AHCI to IDE

* under 'boot' -> 'boot settings configuration' I changed Quiet Boot from enabled to disabled.

* restarted

* hit 'esc' during startup and it allowed me to select my boot device.

voila (i'm not really french though)

---

### Post by PhilGil on 2010-11-22
A couple of suggestions...

To poster #1:
I'm assuming you actually created a bootable thumb drive and didn't just copy the ISO to the drive. Instead of changing the boot order in the BIOS, try hitting the ESC key when the BIOS screen appears then selecting the USB drive from the boot device screen. I don't know why setting the boot order in the BIOS isn't working, but this method works on my EEE PC 1000h.

To poster #2:
I've found Unetbootin to be temperamental with newer Ubuntu releases. If you have access to a desktop computer you might try booting to a live CD and using Ubuntu's native USB boot disk creator.

---

### Post by PhilGil on 2010-11-22
> **Scooter_X said:**
> 

* hit 'esc' during startup and it allowed me to select my boot device.


Oops, see you already figured that one out.

---

### Post by Scooter_X on 2010-11-22
Yea. Sorry. I'm so impatient. ;)

---

### Post by searchfgold6789 on 2010-11-22
Thank you :)
Please mark this as solved.

---

