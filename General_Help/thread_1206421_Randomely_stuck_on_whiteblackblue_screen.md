---
title: "Randomely stuck on white/black/blue screen"
date: 2009-07-07
forum: General Help
---

### Post by gueshew on 2009-07-07
Frist of all let me say that I recently switched to ubuntu and I am totally converted, I love it and would never switch back to windows.
Thank you to everyone who made this amazing OS available to us.

I run 9.04 ubuntu on an acer aspire 3680 laptop. EVERYTHING works great out of the box  or nothing that I haven't been able to solve through a quick search on the ubuntu forum exept something that has been giving me some trouble:

At random times the screen turns completely grey or black or any other unpredictable color and freezes on it. Meaning the whole screen is either completely black/grey/blue etc...

The The OS seems to be still working, meaning if I was watching a video I can still hear the sound, however there is nothing I can do to get out of it exept force re-boot the laptop by holding the power button.

I would greatly appreciate any help as this is the only issue which prevents my from having a seamless experience of ubuntu.

Thank you in advance.

---

### Post by danwood76 on 2009-07-07
Could very well be a graphics driver issue.

Could you tell us the system specs?

Also from a terminal could you output the following command which will list your hardware:
```

lspci

```

---

### Post by moster on 2009-07-07
That is happening when Ubuntu finds out that some app is freezed. He make it look grey.

---

### Post by danwood76 on 2009-07-07
Only the app in question goes grey, not the whole screen.
And he notes different colours.

---

### Post by gueshew on 2009-07-08
Thanks for your responses.

Here are the specs:
                                                                                       [FONT=Arial, sans-serif][SIZE=2]**Platform**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**1**[/SIZE][/FONT]
                                           [FONT=Arial, sans-serif][SIZE=2]Intel[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 Celeron[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 M processor [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**420**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 (1.60GHz, 533 MHz FSB) [/SIZE][/FONT]                 
                 [FONT=Arial, sans-serif][SIZE=2]Mobile                 Intel[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 940GML/943GML Express chipset[/SIZE][/FONT]
                                                                       [FONT=Arial, sans-serif][SIZE=2]**System                 memory**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**1,2**[/SIZE][/FONT]
                                                            [FONT=Frutiger Roman, Courier New][SIZE=2][FONT=Arial, sans-serif][SIZE=2]**1.5**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2] GB of DDR2 [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]533                 MHz [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]memory[/SIZE][/FONT][/SIZE][/FONT]
                                                             [FONT=Arial, sans-serif][SIZE=2]**Display**[/SIZE][/FONT]
                                                            [FONT=Frutiger Roman, Courier New][SIZE=2][FONT=Arial, sans-serif][SIZE=2]**14.1**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**"                 WXGA Acer CrystalBrite**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]™[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 TFT LCD, 1[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]280[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 x [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]800[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 pixel [/SIZE][/FONT][/SIZE][/FONT]
                                                             [FONT=Arial, sans-serif][SIZE=2]**Graphics**[/SIZE][/FONT]
                                                            [FONT=Frutiger Roman, Courier New][SIZE=2][FONT=Arial, sans-serif][SIZE=2]Mobile                 Intel[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 940GML[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]/943GML[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 Express chipset with integrated 3D graphics, featuring Intel[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 Graphics Media Accelerator (GMA) [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]950[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 and up to [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]224[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 MB of shared system memory, supporting Microsoft[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 DirectX[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 9.0[/SIZE][/FONT][/SIZE][/FONT]
                                  [FONT=Arial, sans-serif][SIZE=2]Dual independent                 display support[/SIZE][/FONT]
                                  [FONT=Arial, sans-serif][SIZE=2]16.7 million colors[/SIZE][/FONT]
                                                [FONT=Arial, sans-serif][SIZE=2]**Audio**[/SIZE][/FONT]
                                                            [FONT=Frutiger Roman, Courier New][SIZE=2][FONT=Arial, sans-serif][SIZE=2]Intel[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 High Definition audio support[/SIZE][/FONT][/SIZE][/FONT]
                                  [FONT=Frutiger Roman, Courier New][SIZE=2][FONT=Arial, sans-serif][SIZE=2]S/PDIF[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]4[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 (Sony/Philips Digital Interface) support for digital speakers[/SIZE][/FONT][/SIZE][/FONT]
                                                [FONT=Arial, sans-serif][SIZE=2]**Storage**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]**1**[/SIZE][/FONT]
                                           [FONT=Arial, sans-serif][SIZE=2]**80**[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 GB hard disk drive[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]5[/SIZE][/FONT]
                                  [FONT=Frutiger Roman, Courier New][SIZE=2][FONT=Arial, sans-serif][SIZE=2]5-in-1                 card reader, supporting Secure Digital (SD), MultiMediaCard                 (MMC), Memory Stick[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]®[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 (MS), Memory Stick PRO[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]™[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 (MS PRO), xD-Picture Card[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]™[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]                 (xD)[/SIZE][/FONT][/SIZE][/FONT]
                             

and the lspci report:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

In the compiz settings manager I have disabled "fading windows" "wobbly windows" which seems to have done the trick but it only has been a few hours so I can't be sure yet. It is however an artificial solution which doesn't solve the core issue.

Also the screen turns opaque grey (or any colour), not the type of grey when an app is freezing. I cannot see through the colour, it is just uniformly the same colour over the whole screen, that's all.

Let me know if you need any other info.

---

### Post by moster on 2009-07-08
Well, I do not know about any other valid reason why should any app change its color :)

Now, many people with your graphic card reported problems and that is widely known. Apparently they make that right in next ubuntu. You can wait that or switch to another distro. This is only my opinion, maybe somebody else would tell you something more practical solution.

---

### Post by gueshew on 2009-07-08
Thanks for your response.

No app is changing colour, it is the whole OS which is. The screen turns into different random colours, and it is not transparent. Dark grey all over the screen, and I can't see through that colour.




> **moster said:**
> Well, I do not know about any other valid reason why should any app change its color :)

Now, many people with your graphic card reported problems and that is widely known. Apparently they make that right in next ubuntu. You can wait that or switch to another distro. This is only my opinion, maybe somebody else would tell you something more practical solution.

---

### Post by danwood76 on 2009-07-08
With the drivers that your card uses I think there are quite a few performance tweaks that can be done which may help.

Follow this guide and get the safe configuration:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

This may fix the issue as it has solved many other issues reported by users.

---

### Post by gueshew on 2009-07-13
I had used this guide with the optimal configuration to help when playing full screen videos on youtube which used to stutter and not play smoothly.

I will try to revert to the safe configuration and will let you know the results.

thanks for the suggestion anyways



> **danwood76 said:**
> With the drivers that your card uses I think there are quite a few performance tweaks that can be done which may help.

Follow this guide and get the safe configuration:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

This may fix the issue as it has solved many other issues reported by users.

---

### Post by gueshew on 2009-07-14
I was in fact on the safe configuration.


After upgrading to kernel 2.6.30 (optimal) all my video card troubles went away, and overall my system feels more responsive and sharp.


Thank you so much for setting me on the right track!

---

### Post by danwood76 on 2009-07-14
Glad I could help!

---

