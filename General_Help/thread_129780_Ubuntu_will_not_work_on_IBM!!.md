---
title: "Ubuntu will not work on IBM!!"
date: 2006-02-14
forum: General Help
---

### Post by bigblop on 2006-02-14
I have just got an IBM T40P, but after installing winXP followed by Ubuntu and then installing all the software updates for T40/p the machine will not boot! It only says GRUB in the upper left corner. I cannot even boot from a boot CD since Access IBM or F11 does not have any effect any more!

I have found this:

IMPORTANT NOTE

This is for readers with T40 or T41 notebooks, which try to have all: Windows, working Access IBM and linux.

What is described below this note will work only in case that your IBM PreDesktop Area is in a system partition. (Visible "ordinary" partition of usually 3 - 5GB size, with type ID 0x12.)

Older Thinkpads like T40(p) or T41(p) use a HPA (Hidden Protected Area) instead of this system partition for this PreDesktop Area. Unfortunately the linux kernel disables this area (every time non preventable?) at boot time and if you later choose "Use largest unpartitioned space" during ubuntu installation, you will destroy the HPA. Additionally GRUB will write this "altered" geometry (with disabled HPA) into the MBR. This leads to a totally broken system. After reboot windows will boot to bluescreen (Unmountable Volume) and Access IBM will not work as well. It seems that the special IBM MBR has to be there for accessing the hidden partitions in the HPA. So far, I could not yet install ubuntu (preserving winxp (with security chip on) and preserving IBM PreDesktop Area, with success. Any ideas very welcome. (I will try to partition manually and install GRUB or LILO NOT to MBR and report the results.) 

on this page:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_(1875)#Getting_Access_IBM_to_Work_1](http://www.thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_(1875)#Getting_Access_IBM_to_Work_1)

so it seems that Ubuntu will not work on an IBM T40/P machine!

This is just a warning to everyone else considering this machine!

---

### Post by koolguynet on 2006-02-15
I am sorry to hear you are having problems, but I installed Ubuntu on my T41 with no problems, even wireless worked.  I didn't want to keep windows so I didn't have to worry about the hidden area.  You want to keep a windows partition, right?

---

