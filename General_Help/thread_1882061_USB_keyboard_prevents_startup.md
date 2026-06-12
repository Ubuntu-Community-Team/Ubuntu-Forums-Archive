---
title: "USB keyboard prevents startup"
date: 2011-11-16
forum: General Help
---

### Post by Nico0020 on 2011-11-16
I have a new laptop, so I am getting to go through the fun of figuring strange problems out.  I have a  Dell Inspiron N7110 laptop.  With Ubuntu 11.10 64bit, most things work out of the box.  

One strange problem I am facing is, if I have a USB keyboard plugged in during Ubuntu startup, the screen will eventually shut off.  I am not sure if the entire system is refusing to boot as I can't tell what is happening after that.  It only seems to be the USB keyboard that does this, as I have a USB wireless mouse dongle plugged in 100% of the time that never causes issues.  Anyone have any idea why this is an issue and how to get around it?

---

### Post by mister_playboy on 2011-11-16
Do you have USB booting disabled in the BIOS?  I can't boot with my USB HDDs plugged in on 11.10 unless I have USB booting turned off.

---

### Post by Nico0020 on 2011-11-16
I dont have an option for that.  The only USB options I see are USB emualtion, USB power sharing, and to disable usb alltogether. I updated my bios to the most recent version, but no such options.

---

### Post by mister_playboy on 2011-11-16
I suppose another possibility would be: if you have a boot device priority list in the BIOS, make sure your internal hard drive has greater priority than any of the USB entries.

---

### Post by Nico0020 on 2011-11-20
internal HDD is set as the highest, followed by disc drive, then usb.  Still having issues sadly.

---

### Post by ki4jgt on 2011-11-20
The keyboard may be faulty. I had a computer monitor once which shut down the entire computer every time a program was started. It turned out that one of the pins in the monitor's cord was bent and causing problems.

---

