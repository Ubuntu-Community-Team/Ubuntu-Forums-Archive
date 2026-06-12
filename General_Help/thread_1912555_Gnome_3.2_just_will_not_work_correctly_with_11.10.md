---
title: "Gnome 3.2 just will not work correctly with 11.10"
date: 2012-01-20
forum: General Help
---

### Post by thechad90000 on 2012-01-20
Hello,

I'm a relative noobie and I've searched but couldn't find any help with the problems I'm having. I really liked the 3.2 desktop environment when I was testing Ubuntu but I just wiped my Windows operating system and am only using Ubuntu 11.10 now. However, when I tried to get the gnome-shell, it works but it's not the same as it was when I was testing it.

I've uploaded a screenshot. If put the mouse in the top left corner, the whole dashboard configuration doesn't pop up either. I've uninstalled it and reinstalled it multiple times. I'm logged into the correct desktop environment from the original login screen as well.

Any help would be really great. Thanks.

---

### Post by Frogs Hair on 2012-01-20
Hello and Welcome 

It looks like you have logged into Classic Gnome instead of Gnome . Logout or restart and select Gnome from the session menu .

---

### Post by thechad90000 on 2012-01-20
See that's what I'm logged into right now. I tried logging into all the different ones. The one that I used to log into the Gnome 3.2 desktop was just labeled GNOME. That's what I'm logged into here and it's just this. Gnome Classic looks the same.

Edit: Also thank you for the kind welcome.

---

### Post by Frogs Hair on 2012-01-20
There are some graphics cards that don't support the Gnome Shell , but it seems odd that you were able to test it and not have it work. . Did you test via the live cd , Wubi , or virtual box software of some kind ? 

I would also check additional drivers and see if there is a recommended proprietary driver for your graphics card / chip  if not already installed .

---

### Post by thechad90000 on 2012-01-20
I tested it with Wubi and it worked perfectly fine.

---

### Post by thechad90000 on 2012-01-20
I've also checked to see if there are additional drivers that are needed. I installed one of them but the other keeps giving me an error everytime I try to install it. Like I said, the desktop worked fine in Wubi.

I hope I can get this fixed. The Gnome 3 desktop really got me interested in giving Linux a try.

The screenshot is the error message I keep getting when trying to install the top driver.

---

### Post by Double.J on 2012-01-20
Hi there, if you've added drivers, restarting may help? Which driver are you having difficulty installing?

---

### Post by thechad90000 on 2012-01-20
I have restarted. The one driver that won't install ATI/AMD proprietary FGLRX graphics driver (post-release update).

The ATI/AMD proprietary FGLRX graphics driver itself installs just fine but the other one gives the error message I posted. Like I said though, I don't know if that'd be the issue seeing as it worked perfectly fine while I was using it in Wubi.

---

### Post by Frogs Hair on 2012-01-21
I don't know what to do other than look at the log file as suggested by the error message . I have no idea why Wubi works and a traditional dual boot doesn't  . They are both dual boots except Wubi installs Ubuntu inside the Windows partition and uses the Windows boot loader .

Run the following command in the terminal and post the output via copy and paste in code tags using # symbol on the reply box tool bar .```
lspci
```

---

### Post by thechad90000 on 2012-01-21
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB Controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```

---

### Post by Frogs Hair on 2012-01-21
There should be no problems with AMD HD 6470M graphics chip / card listed in the output . The reason the driver wasn't able to install lies in the log file viewer .

I can only suggest reinstalling again  ,   but this time delete the configuration folder from the the file system . Use the following command to open the file system as root . ```
gksudo nautilus
```
Navigate to file system and next to usr/share/gnome shell and remove the folder before reinstalling .

---

### Post by thechad90000 on 2012-01-21
This didn't work either. I just don't understand how it could've worked before but not now.

---

### Post by Frogs Hair on 2012-01-22
It is possible that there may be a problem with the Ubuntu ISO , which is only affecting the Gnome shell installation . Did you run a checksum ? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by thechad90000 on 2012-01-22
> **Frogs Hair said:**
> It is possible that there may be a problem with the Ubuntu ISO , which is only affecting the Gnome shell installation . Did you run a checksum ? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Hmm...I'm not sure about that. I wiped my entire other drive so I don't have the .iso anymore. I've just got the DVD that I burned the .iso to. Can I use the check for that or would you recommend downloading another .iso and reinstalling the operating system?

btw..I can't thank you enough for your help. For people who are so new to this like I am a community like this is wonderful and helps a ton.

---

### Post by Frogs Hair on 2012-01-22
I just can't think of anything else except the installation cd may be bad . If the shell worked with Wubi it should work with a traditional dual boot .
You already know the shell runs on your hardware . If it is not too much work and you really want to use the shell it may worth a trying a new cd. A couple hours creating a new disk and installing beats waiting days for a possible solution .

---

### Post by thechad90000 on 2012-01-22
> **Frogs Hair said:**
> I just can't think of anything else except the installation cd may be bad . If the shell worked with Wubi it should work with a traditional dual boot .
You already know the shell runs on your hardware . If it is not too much work and you really want to use the shell it may worth a trying a new cd. A couple hours creating a new disk and installing beats waiting days for a possible solution .

You may be right. I've just had so much fun customizing this and everything I'd hate to go back to the beginning but I've got to do what I've got to do then. Thanks a ton.

---

### Post by West201 on 2012-01-22
> **thechad90000 said:**
> You may be right. I've just had so much fun customizing this and everything I'd hate to go back to the beginning but I've got to do what I've got to do then. Thanks a ton.

I have very similar video cards to yours. I don't have Ubuntu installed, but I do use Linux Mint 12 (based on Ubuntu 11.10) on virtualbox, and I received the exact message when installing the video drivers, and the font would disappears and the panels as well. They installed fine on Ubuntu 11.04 and Linux Mint 12 without any issues. 

The only solution I found was not installing the ATI card drivers. :(

---

