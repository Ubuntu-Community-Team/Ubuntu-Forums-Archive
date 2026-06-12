---
title: "ubuntu live cd"
date: 2010-02-03
forum: General Help
---

### Post by serviam on 2010-02-03
I have a question. I have downloaded the current version of ubuntu to my computer. I then burn the os as a live cd via infrared recorder. When I insert the cd to the cd drive, and reboot the computer, nothing happens. What should I do?

---

### Post by hemimaniac on 2010-02-03
Is the computer set to boot frm the CD/DVD drive @ boot? may need to check you bios settings.

---

### Post by Ordes on 2010-02-03
Did your burn it as an image? Or did u just burn the data?

When you look in your cd, what do you see?
1) xxx.iso
or
2) multiple files and folders? like casper

if you see (1) than you just burned the data, and you have to reburn as image.

If you burned it as an image, make sure you enabled boot from CD-ROM, and in the boot hierarchy your CD-ROM is listed above HDD.

If you have all this and its still not working, than it might be a bad burn.

---

### Post by TBABill on 2010-02-03
When you boot up your computer you should have an option on the opening screen to press xxx for help. On mine it's "F2" that takes me into my bios settings. Within the bios settings you need to move the boot sequence around to place the CD drive to boot BEFORE the hard drive. That way the system sees the bootable disk in the CD drive and boots from it rather than using the system installed on the hard drive.

If you burned the disk correctly then changing your bios settings should work. If not, make sure you research how to burn a .iso as an image. There are plenty of posts on how to do it.

---

