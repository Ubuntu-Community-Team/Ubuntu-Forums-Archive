---
title: "Very Slow Boot on Ubuntu 10.10"
date: 2011-01-08
forum: General Help
---

### Post by irfan01 on 2011-01-08
Hello,
I using ubuntu 10.10 but booting is very slow.
Login screen showing after 25-40s~
After i enter login details, background showing 43s~

Here is my bootchart: [http://www.ressim.net/61/upload/148dc1a9.png](http://www.ressim.net/61/upload/148dc1a9.png)

(I using wlan0)

---

### Post by irfan01 on 2011-01-08
Any reply please :(

---

### Post by irfan01 on 2011-01-08
Flood but needed to bump :(

---

### Post by wilee-nilee on 2011-01-08
Read the COC it is a 24 hr bump rate asked for. So it looks like about a 35 second boot to the login, is this correct?

---

### Post by irfan01 on 2011-01-09
> **wilee-nilee said:**
> Read the COC it is a 24 hr bump rate asked for. So it looks like about a 35 second boot to the login, is this correct?
Yes. After i delete virtualbox, boot time lowered to 35 sc. But this is slow :(

---

### Post by oldfred on 2011-01-09
Why do you think 35sec is slow? Only SSD's that do not load anything will be quicker. 

My system takes a little less than a minute with loading a lot of drives. With windows XP it is 4 minutes and hibernation from windows is over a minute.

---

### Post by MetroPietro on 2011-01-12
I have a series of problems and performance-regressions since upgrading to 10.10. Have been trying to find webpages where these problems are discussed.

1.The boot process hangs for at least half a minute, at various different stages, unless a keyboard key is pressed or a mouse/trackpad is jiggled. The hard drive activity-light just goes dark. 

2. When system is up and running, audio playback is choppy and it is difficult to enter "suspend" mode. Cursor occasionally locks up; have to press the Power button just to remind the laptop to resume running.

The problem seems to be the power-saving feature in newer kernels. It seems to clash with my laptop.

Shortly after upgrading from 10.04 to 10.10, I started troubleshooting this problem and installed Kernel 2.6.36-020636-generic. I made sure that HDD was set from SATA to Compatible Mode in the BIOS. I tried to shut down the power-saver mode [nohz=0 or something like that in a GRUB config file]. That made the system useable. But I expected that in the following three months that there would be better troubleshooting of these problems. I have seen many complaints about performance regressions on 10.10, but none that fix the tendency of my system to 'hiccup' in its performance.

---

### Post by MetroPietro on 2011-01-12
Follow-up: turns out I missed some fine print. I'm using a Toshiba NB205 Netbook, which I bought in Aug 2008 and thus began with Ubu 8.04. 8.04 booted with GRUB 0.96 or earlier. When I upgraded to Ubu 9.10, I opted to keep legacy GRUB rather than update to GRUB2, because there were lots of complaints about GRUB2 and few solutions available then.

A year later, the newer kernels being issued with 10.10 have power-saving features that cannot be disabled with legacy GRUB, so far as I can tell. Making the adjustments in GRUB2 (1.96 and later) are straightforward.

Instructions for upgrading from legacy GRUB (0.97 and earlier) to GRUB2 (1.96 and later) are [here]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202").

Instructions for adjusting Ubuntu to improve boot times and other features on Toshiba NB205 Netbooks are [here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205").

---

