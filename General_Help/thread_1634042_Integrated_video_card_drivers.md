---
title: "Integrated video card drivers?"
date: 2010-11-30
forum: General Help
---

### Post by [G]13 on 2010-11-30
Hi I installed ubuntu on an old compaq pc and i'm having a lot of video errors and crashes. I'm pretty new to it all and i'm just wondering if there's any integrated video drivers. Thanks for your help in advance!

---

### Post by Yellow Pasque on 2010-11-30
Need more info. Post /var/log/Xorg.0.log, or at least the output of glxinfo so we know what kind of GPU you have.

---

### Post by [G]13 on 2010-11-30
> **Temüjin said:**
> Need more info. Post /var/log/Xorg.0.log, or at least the output of glxinfo so we know what kind of GPU you have.

I'm sorry... but I really have no clue what that means. Can you tell me how to do this?

---

### Post by mastablasta on 2010-11-30
You didnt' give any information appart from saying your computer doesn't work. it's liek saying my car is broken, what's wrong?
 
Read this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
And then do this - go to: Applications -> Accessories -> Terminal
 
when the terminal opens type in:
```

lspci | grep VGA
```
 
or this:
```
 
lspci

``` 
copy the output information and then post it here between code tags (mark the texs and click on # sign when you form your reply). then we can continue with possible solutions.
 
 Note: these two commands will give use information about what kind of hardware you are using in your computer.
 
edit: also important info is how did you install it (wubi? normal install?)

---

### Post by [G]13 on 2010-11-30
Ok here's what I got, and I'm sorry the issue i'm having is that every time the video is stressed to do something I.E pulling up flash games, or pictures, or videos. It throws a large display of random colors in a "rainbow" across the monitor. I call it robot jizz :P

#00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)#


And Ubuntu was installed from a flash drive. Is there any other info I can post?

---

