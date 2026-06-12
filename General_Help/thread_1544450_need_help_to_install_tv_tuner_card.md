---
title: "need help to install tv tuner card"
date: 2010-08-02
forum: General Help
---

### Post by chinmay3 on 2010-08-02
[SIZE=2]i am new to ubuntu. i recently installed ubuntu 10.4 distro. i want to install my winfast tv 2000xp expert tv tuner on it , but don't know how to do that. i searched forum but nothing find useful. please help me. please give me detailed installation information.

*tv tuner specification:*
winfast tv2000 xp expert
Chipset: conexant CX2388X series
Hardware Interface: 32 bit PCI 2.3 bus mastering
                                 plug & play compliant
Video standard : NTSC , PAL , SECAM

[/SIZE]

---

### Post by oldos2er on 2010-08-02
Can you run **lspci** in a terminal, and post the output here?

---

### Post by chinmay3 on 2010-09-11
[COLOR=Black]ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:03.0 Modem: Smart Link Ltd. SmartPCI2800 V.92 PCI Soft DFT (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

sorry for such a long delay to your response . this what i got when i typed lspci in terminal . please help me . once again thanks for your help.:):KS
[/COLOR]

---

### Post by fragos on 2010-09-12
01:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

Thats your TV card. All that's left is install a TV viewer. Which viewer can depend on the driver loaded for your card. Run "lsmod |grep tv" in a terminal window. If bttv is displayed, install TVtime and it'll handle all the details for you. That's the one I use. If you didn't get bttv then try installing mythtv. You can search the forums to get help with installing MythTV.

---

### Post by chinmay3 on 2010-09-16
Thanks a lot.
you are genius. I installed TVtime & its working so nicely.
Due to people like you , who are always helpful I becoming great fan of ubuntu .
Now I can completely switch to ubuntu . As I was unable to watch tv on ubuntu I have to keep windows as first option. But now I can remove windows.

once again thanks....

---

