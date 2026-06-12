---
title: "Format two harddrives: Put them together or install separated systems on each one"
date: 2010-10-13
forum: General Help
---

### Post by atahu on 2010-10-13
Hi,

I have two harddrives. I will install on the first one ubuntu and on the other one opensuse or I will even put them together. I dont know yet.

Has somebody experiences with booting two harddrives, how can I choose between them? And when I delete one with gparted, will the free memory be automatically placed to the not deleted harddrive?

---

### Post by dcstar on 2010-10-13
> **atahu said:**
> Hi,

I have two harddrives. I will install on the first one ubuntu and on the other one opensuse or I will even put them together. I dont know yet.

Has somebody experiences with booting two harddrives, how can I choose between them? And when I delete one with gparted, will the free memory be automatically placed to the not deleted harddrive?

Hard drives have absolutely nothing to do with "memory".

---

### Post by atahu on 2010-10-13
okay, how can I put dev/sda and dev/sdb togehter?

---

### Post by Sylslay on 2010-10-13
Eeasy way!!

Install one OS and one drive at time.

1st Ubuntu, on faster/biger hdd.
2nd. Disconnect 1st drive and replace it w 2nd, and install Open Suse.

Ubuntu drive must be set as master and OpenSuse as slave.

After both installation complite, connect both drive master and slave to IDE cable.

When ubuntu start run in console command

sudo os-prober 
sudo update-grub2

Both OS should be now in bootloader menu.!!!

Second method non-hardwere skill require, install 1st pleace OpenSuse on any drive and do not isntall Grub (should be somewhere in Advance option), again do not install bootloader

after this install Ubuntu, but when it ask for partition for use, go for manual option and format 2nd hdd.

---

### Post by Sylslay on 2010-10-13
Answer for second ????

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

But how than install both OS on that kind partiton? Both installators need to be able use LVM!!!

---

