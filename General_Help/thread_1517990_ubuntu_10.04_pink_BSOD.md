---
title: "ubuntu 10.04 pink BSOD"
date: 2010-06-25
forum: General Help
---

### Post by rollaster on 2010-06-25
I downloaded an x64 version of the latest ubuntu 10.04 desktop. Burned it to a DVD at 1x speed in DVD Decrypter and upon booting up I got a pink screen that would sometimes change colors to purple, black, or grey. I thought it was a bad DVD so I burned another copy, didn't work. Maybe my download got corrupted and re downloaded it and burned it again didn't work. 

Used the universial usb installer to install the iso to my new usb key which i removed all the contents before installing. This time I get to the black menu screen, except when I go to install to hard disk I get that same error again. Pink/purple screen most the time and flickering for the bottom 3/4 of my screen. If I reboot my pc the flickering still persists even in the BIOS and windows. I have to either reinstall my nvidia driver or wait like 20mins for it to fully dissipate.

p5w-dh deluxe (latest BIOS drivers)
2TB SATA I'm trying to install it on. I shrunk the partition down by 100GB to install ubuntu and pcbsd for each 50GB.
I got windows 7 x64 and xp 32bit on the same hard drive which I arragned with EasyBCD
e6600 
8800gtx (latest windows drivers)


After all this I installed ubuntu 9.10 x64 on a DVD and pcbsd aswell they both installed perfectly no problems at all. Ubutnu I think installed on a different hard drive because it didn't detect the free partition space. There is defiantly something at least to my knowledge with the ubuntu DVD but it only appears on my hardware and temporary BIOS flickering is beyond strange. 

So I'm wondering how I can troubleshoot this? I waited till ubuntu 10.04 came out to install ubuntu and I'm stuck with 9.10. And I'm very afraid to upgrade for this reason. The last think I want is a pink screen unable to be repaired because the USB/DVD won't work. Or should I wait for a more stable release or is ubuntu 10 crap all-together?

---

### Post by dcstar on 2010-06-25
> **rollaster said:**
> 
.........
**If I reboot my pc the flickering still persists even in the BIOS and windows.**
.........
So I'm wondering how I can troubleshoot this? I waited till ubuntu 10.04 came out to install ubuntu and I'm stuck with 9.10. And I'm very afraid to upgrade for this reason. The last think I want is a pink screen unable to be repaired because the USB/DVD won't work. Or should I wait for a more stable release or is ubuntu 10 crap all-together?

Do not blame Ubuntu for problems with your hardware, Ubuntu has nothing to do with what happens in your BIOS or Windows.

---

### Post by rollaster on 2010-06-25
> **dcstar said:**
> Do not blame Ubuntu for problems with your hardware, Ubuntu has nothing to do with what happens in your BIOS or Windows.

Yeah I know, but it is really strange. After this pink BSOD happens when I boot up with either a USB or DVD and I reboot and take the disc or USB out. And during that pink bsod like 3/4 of the buttom is flickering really fast. It's not as bad when I reboot and take the disc out but it still persists. I really don't care either way, its not causing damage to my pc, but it is beyond weird. My hardware is all fine I've had all my parts and running windows for about 2 months, before that I made some upgrades which is why I reformatted. 

But anyways how does one troubleshoot this weird issue? Only Ubuntu 10.04 x64 desktop edition cannot boot at all and I get this pink BSOD. Top quarter is fine, buttom 3rd of the screen is flickering, when ubuntu 10.04 should be loading. Ubuntu 9.10 doesn't encounter this problem at all.

---

### Post by ubunterooster on 2010-06-25
Does it appear to be overheating at the time?

---

### Post by dcstar on 2010-06-25
> **rollaster said:**
> 
.........
But anyways how does one troubleshoot this weird issue? Only Ubuntu 10.04 x64 desktop edition cannot boot at all and I get this pink BSOD. Top quarter is fine, buttom 3rd of the screen is flickering, when ubuntu 10.04 should be loading. Ubuntu 9.10 doesn't encounter this problem at all.

Do not just reboot, totally power off by removing the power cable for at least 30 seconds to reset the hardware.

---

### Post by rollaster on 2010-06-25
> **ubunterooster said:**
> Does it appear to be overheating at the time?

I run speedfan on windows. CPU OC @ 3.0ghz have some custom thermal grease applied

Runs at 40C @ full load tops
GPU 60C
all hard drives 33C or under

so no

---

