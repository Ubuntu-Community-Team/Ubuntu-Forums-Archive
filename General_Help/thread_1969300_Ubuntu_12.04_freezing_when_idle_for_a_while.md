---
title: "Ubuntu 12.04 freezing when idle for a while"
date: 2012-04-29
forum: General Help
---

### Post by Kojy on 2012-04-29
Hello folks! after the upgraded the OS from Ubuntu 11.10 to Ubuntu 12.04, I'm having a problem. When the pc still idle for a while, the OS freeze, and I need to shutdown forced through the button. Someone can help me about this?

---

### Post by LakeWind on 2012-04-30
Is this on a laptop or desktop? How long is the pc idle before it freezes? Sounds like it could be a driver issue.

Have you tried changing your lock settings? "System Settings" > "Brightness and Lock"... turn off "Lock". Also if this is a laptop, try unchecking "Dim screen to save power". 

If this problem persists, I would recommend you back up all your important data and try doing a clean install of 12.04.

---

### Post by LakeWind on 2012-04-30
Forgot to mention when editing your "Brightness and Lock" settings, there's also a setting to "Turn screen off when inactive for:" I believe it defaults to 10 minutes. Select "Never" and see if that helps with the freezing issue.

---

### Post by Kojy on 2012-04-30
LakeWind, it's a Desktop. Pc stay idle more or less 10 min. I alredy tried to change my lock screen settings.
Also, its a clean install version. In Brightness and Lock menu, I selected "Never" to "Turn Screen Off When Inactive For" option, also is selected "off" to lock. There is not "Dim screen to save power" option, it's not a laptop =/. Format is not an option, cuz I work on it, and all the configuration is set up for me, I'll take a long time to set again.

---

### Post by geoaraujo on 2012-04-30
I don't know if it is the same issue, but it's happening on my Kubuntu 12.04 too. :(

---

### Post by ilMede on 2012-05-01
Hi,
I have a similar problem. After a clean install of 12.04 it happens very often that the system is completely stuck after a random amount of time. It might happen after a minute or after an hour, but it always happens. The only solution is the power button.

Basically the video is still on, but is impossible to move mouse or to use keyboard (not sure maybe is a monitor freeze).
I checked the system/kernel logs, but they don't contain any error.
Please help..

My laptop is  Toshiba Equium A200-1V0
Processor	 type : Intel® Pentium® Dual-Core Processor T2310 
clock speed : 1.46 GHz 
Front Side Bus : 533 MHz 
2nd level cache : 1 MB 
Operating System / Platform	
Genuine Windows® Vista® Home Premium Edition

System memory	 standard : 2,048 (1,024 + 1,024) MB 
maximum expandability : 2,048 MB 
technology : DDR2 RAM (667 MHz) 
Hard disk	 capacity : 120 GB 
certification : S.M.A.R.T. 
drive rotation : 5,400 rpm 
DVD Super Multi drive (Double Layer)	 compatibility : CD-ROM, CD-R, CD-RW, DVD-ROM, DVD-R, DVD-R(DL), DVD-RW, DVD+R, DVD+R(DL), DVD+RW, DVD-RAM 
maximum speed : Read: 24x CD-ROM, 8x DVD-ROM/ Write: 24x CD-R, 4x CD-RW, 10x HS CD-RW, 16x US CD-RW, 8x DVD-R, 4x DVD-R (Double Layer), 6x DVD-RW, 8x DVD+R, 4x DVD+R (Double Layer), 8x DVD+RW, 5x DVD-RAM 
type : DVD Super Multi (Double Layer) drive 
Display	 size : 15.4 " 
type : Toshiba TruBrite® WXGA TFT display 
internal resolution : 1,280 x 800 
Graphics adaptor	 type : Intel® GMA X3100 
memory : up to 358 MB total available graphics memory with 2 GB system memory 
memory type : shared 
Internal video modes	 The following internal video modes are supported: 
resolution : 1,280 x 800 
maximum number of colours : 16.7 Million 
Max External Video Modes	 Max Resolution : 2,048 x 1,536 
Max Colours : 4.3 billion 
Max Refresh Rate : 85 Hz 
Non-interlaced resolution with max refresh rate : 1,600 x 1,200 
Interfaces	 1 × DC-in 
1 × external monitor 
1 × RJ-45 
1 × external microphone 
1 × headphone (stereo) 
2 × USB 2.0 
Expansion	 2 × memory slots 
1 × ExpressCard slot 
Wireless communication	 Compliancy : Wi-Fi® 
Network Support : 802.11b/g 
Manufacturer : Realtek 
Wireless Technology : Wireless LAN 
Wired communication	 topology : international V.92 modem 
speed : 56 Kbps data and 14.4 Kbps fax 
topology : Ethernet LAN 
speed : 10BASE-T/100BASE-TX

---

### Post by mckenzis on 2012-05-01
I too am having this problem.

I have an AMD64 based system and upgraded from 11.10 (which had been upgraded from (11.04)). I never experienced this with either previous version.

I have an NVIDIA video card.

I checked through the logs but don't see anything that stands out.  

As per other users, I have to hit the reset button to recover!

---

### Post by brianpb on 2012-05-21
I have this same problem. Occurs after an upgrade from 11.10 to 12.04. I have a Dell E6420 laptop. Freezes ~twice per day while I am away.

---

### Post by vectorboson on 2012-05-21
I believe I have this same issue. The entire system will freeze when I'm  not looking at or interacting with it; sometimes when it's doing  something (e.g. compiling), sometimes when it's just sitting around - in  any case it happens even with suspend and brightness reduction turned  off. This has happened with a wide variety of applications open, and it  does not seem to have anything to do with any individual programs. The  system does not respond to sysrq commands when it has locked up in this  way. The machine is an essentially brand new HP Pavilion dm1-4010us, and  it has done this in both a 64-bit installation upgraded from 11.10 and a  32-bit fresh installation of 12.04. I have not encountered any issues  on Windows 7.

System specs are:
AMD E-450 Processor
4GB RAM, memtested and it's fine
Radeon HD 6320 Graphics (freezes have happened both with open-source and with proprietary drivers)
Broadcom BCM4313 Wireless controller, which has given me trouble before on 11.10

Though  I am by no means an expert, I suspect the wireless controller may be  related somehow: on 11.10, before I used the driver workaround in the  networking support forum, I was getting much more frequent lockups along  with unacceptably terrible wi-fi performance. The sysrq keys DID work  for these lockups. Once I did the driver override, wi-fi performance  dramatically improved and the lockups became more like the ones  described here, and sysrq no longer worked during them. I notice that  the wi-fi fix appears to be applied by default in 12.04, as I did not  have to do anything to get acceptable performance out of it when I  reinstalled.

Anyone who has any theories or ideas for additional  tests to perform, let me know and I'll try them as I'm able. I use  Ubuntu for work and this is really making it hard to get anything done.

---

### Post by atom715 on 2012-05-27
I too have the same problem, on a compaq laptop. I did a clean install on my pc to ubuntu 12.04.  The only thing that ever works is the external mouse that i use.  i cannot click on anything and this usually happens when my computer is idle after several hours.  i leave my pc running for hours and sometimes days before this may occur.  i have my brightness and lock settings set to never and not to change anything when the lid is closed.  any help would be greatly appreciated.

---

### Post by utrading on 2012-05-30
For those of you who experienced freeze with 12.04, if you use ivy bridge cpu and intel graphics (HD2000/3000/4000), you may want to upgrade kernel to 3.3.6 or 3.4.0. Check out the link below:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/993187/comments/91](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/993187/comments/91)

This is a well known bug that exists in stock 12.04 kernel. I ran into hard lock up or freeze, especially when virtualbox is running. After upgrading to kernel 3.4.0, it has been rock stable for more than a week.

i5 3570K
Asus P8Z77-V Pro
GSkill 4x4G
Seagate 500G

---

