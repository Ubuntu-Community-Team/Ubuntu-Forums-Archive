---
title: "Ubuntu on a flash drive"
date: 2011-05-14
forum: General Help
---

### Post by GSI on 2011-05-14
Hello. I have an 8GB PQI U172P
 flash drive and I want to intall ubuntu on it for a test. So my question is, If I install ubuntu, will the flash drive last (I mean there will quiet a lot read/write cycles).Will I kill the flash drive by doing this?

Thanks in advance :P

---

### Post by snowpine on 2011-05-14
Theoretically your flash drive will wear out eventually. However it will probably take years, and flash drives are very cheap to replace. :)

I have a cheap 8gb flash drive that I've been using for years to test Linux distros. It hasn't worn out yet...

---

### Post by GSI on 2011-05-14
Yes, ofcourse it will wear out someday... xD Soo.. its safe to install?

---

### Post by snowpine on 2011-05-14
Instructions are here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by howefield on 2011-05-14
You are not likely to get a better answer than you have been given.

Yes it's safe and yes the drive will wear out eventually, but you'd have to be pretty unlucky to ruin your flash drive with a test install and use of Ubuntu. 

You can create the drive with the Startup Disk creator which will function like a Live CD, (which can be done with persistence, allowing you to save files, applications and settings to the drive) or do a "normal" full install to the drive.

---

### Post by GSI on 2011-05-14
I did everything according to the instructions, but I cant get it to boot.. :( I dont know why.. the PC supports booting from USB, I tried both USB HDD and USB ZIP and still nothing.. I end up booting windows :(

---

### Post by snowpine on 2011-05-14
You need to access the boot options in your BIOS and choose the correct device. The key you press depends on your computer. Usually it is Esc, Del, or one of the Fn keys.

---

### Post by Cowchip7 on 2011-05-14
I have an ubuntu mini with a SSD Hard Drive and have been running Ubuntu for over 2 years. Plus, I have been using EXT4 for about a year.

---

### Post by C.S.Cameron on 2011-05-14
If you do the math, 10000 + writes x 16 GB per write x 10 min / GB = 666 40 hour work weeks of use, the life expectancy of a flash drive running Ubuntu should be over ten years.

---

### Post by GSI on 2011-05-15
Still not working.. I did what you guys told me, entered the boot menu and I now know that  the computer identifies the flash drive as "USB-ZIP". I plug the flash drive in, selec USB-ZIP from the menu and hit enter.. a small pause and than it says "Boot error" nothing more, nothing less... just "boot error"

---

### Post by GSI on 2011-05-15
Tried on a laptop, works fine, starts booting and than : 

**(initramfs) unable to find a medium containing a live file system**

:(

---

### Post by snowpine on 2011-05-15
Your USB device is not correctly prepared. Review these steps carefully (especially Step 2):

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Some users have better luck with Unetbootin:

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by C.S.Cameron on 2011-05-15
Check the iso's MD5SUM.
If you used Startup Disk Creator to install to USB try UNetbootin and vice versa.
On my computers I need to set the flash as first hard drive in BIOS.

---

### Post by GSI on 2011-05-16
Nvm.. got the LTS version running :)

---

### Post by Cowchip7 on 2011-05-28
> **GSI said:**
> Nvm.. got the LTS version running :)

Rock on! :guitar:

---

