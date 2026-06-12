---
title: "Ubuntu freezes at purple screen ,but on force re-boot , BusyBox shell comes"
date: 2012-05-06
forum: General Help
---

### Post by alamban on 2012-05-06
I tried both Ubuntu 11.04,11.10 & 12.04. It frequently  freezes at the purple screen (the screen before the 5-dot ubuntu screen)  I wait for 10-15 mins and when I force re-boot, it ends up showing the **Ubuntu BusyBox** black screen with **initramfs** prompt. I checked many forums and many of them said to try this out----> 1.Boot using Ubuntu LiveUSB
2.In terminal, 
  [INDENT]   sudo fdisk -l
 [/INDENT]  I see sda7 as my linux partition ( I hv windows 7 also installed)
  [INDENT]   sudo fsck /dev/sda7
 [/INDENT]  It shows many things.One of them I remeber is "Recovering journal"
  and press ENTER for whatever questions asked during the process.Now  when I go back ,remove liveUSB and boot Ubuntu normally,it works  fine.But the same problem (freezing at the purple screen->force  reboot->ends in BusyBox) comes up after 2 or 3 re-boots.
  No problems when I install ubuntu 10.04 or 10.10. Then I thought it  might be a problem with the kernal I m using.So I installed the kernal  which ubuntu 10.10 uses, but it was of no use.The problem still remains.
  Someone please help. Thanks in advance

---

### Post by Paddy Landau on 2012-05-07
Did you upgrade from 10.04 or was 12.04 a fresh installation?

---

### Post by kjromm on 2012-06-30
I just spent 2 days with this and similar problems when I decided to rebuild my version of 12.04. I decided to do that after it had become unstable and I was losing files and profiles. I assumed it was a software problem, it was not. After numerous attempts to reboot in Ubuntu from a cd after making a new live cd, since I thought there might be a problem with the one I had recently made, I decided to go with a usb boot. While I was waiting for the usb drive to be created on another computer I ran my gparted live 0.81-3 .iso disc and it booted fine. I ran the comprehensive memory test that is part of that package and found I had a bad memory stick. Apparently the built in memory test in the bios was ignoring the problems and letting things go on. Once I changed out the bad memory, everything is working fine. The computer is a Dell Optiplex GX620 with an Intel duo-core processor. I have 3Gb ram and a 150 Gb harddrive.
The lesson here is never assume anything. I hadn't seen memory fail in use in over 30 years! It used to be a common occurrence  but now it is not! If you think it should be working, don't forget to check the hardware!

Ken

---

