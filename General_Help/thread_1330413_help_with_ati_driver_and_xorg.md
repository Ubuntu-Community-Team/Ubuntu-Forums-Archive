---
title: "help with ati driver and xorg"
date: 2009-11-18
forum: General Help
---

### Post by buntuchimp on 2009-11-18
Hi, I am new ubuntu user. I am having issues with a fresh install of 9.1 and my radeon x1600 card. When ever I move or open a window on desktop the cpu starts thrashing (xorg) for several seconds resulting in very slow desktop performance.

From what I have read so far this seems to be an issue with xorg and the default radeon driver. There are some changes to the xorg.conf that some have reported to solve this problem.

My question is this - my 9.10 install did not create a xorg.conf file. I am not sure where xorg gets its parameters from in this case. If I somehow create a xorg.conf will xorg even read it upon start up? If so, how would I create or generate a xorg.conf file - I have seen some samples posted but some sections seem specific to another ati card and it is not clear what I should change those entries to for my card.

It seems like my options are:

1 change xorg configuration - don't know how
2 downgrade xorg - don't know how, not desirable
3 get a new non ati video card - not desirable
4 install windows -defeats the purpose

TIA for suggestions. Please let me know if there is a more suitable forum for this question or maybe some other resources to find help at.

---

### Post by khelben1979 on 2009-11-18
Downloading the driver from the ATi homepage will make the configuration script create an xorg.conf file for you, [look here]("http://support.amd.com/us/gpudownload/Pages/index.aspx"). I can't tell you what driver you should download until you reveal more about your hardware configuration and:
```
lspci
```
will show us this. Type it from a text shell such as [xterm]("http://en.wikipedia.org/wiki/Xterm") or similar.

---

### Post by buntuchimp on 2009-11-18
Thanks. My understanding from what I have read is that the proprietary ATI driver does not support this (or any older than ~6 months) card. Anyways my card is x1600Pro AGP and I am running 32 bit ubuntu 9.1.

Here is lspci:

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

---

### Post by Tickborn on 2009-11-18
HI,
maybe you want to have a look at the discussion in the posts of "**[[B]Compiz Desktop Cube won't work**]("http://ubuntuforums.org/showthread.php?t=1326290")**"**

[]("http://ubuntuforums.org/showthread.php?t=1326290")[/B]

---

### Post by khelben1979 on 2009-11-18
According to what I can see, Catalyst 9.3 support your video card. Look [here]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English"). The driver was released the 26th of march this year.

---

### Post by buntuchimp on 2009-11-18
Ok, the 9.3 catalyst driver does work with my card but not with the xorg included in 9.10 (1.6 i beleive). It seems the only solution is to downgrade xorg.

---

### Post by Zoot7 on 2009-11-18
> **buntuchimp said:**
> Ok, the 9.3 catalyst driver does work with my card but not with the xorg included in 9.10 (1.6 i beleive). It seems the only solution is to downgrade xorg.
Yeah anything newer than Catalyst 9.3 doesn't support your card, and low and behold Catalyst 9.3 ain't compatible with the version of X that's in either Karmic or Jaunty.
Here's a guide on how to downgrade X to suit your needs.
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

It's for Jaunty, but i'm guessing it'll work in Karmic too. It basically says use Intrepid's repos to download and install the appropriate version of X.
Not sure how you'll get on, but it's worth a shot.

---

### Post by buntuchimp on 2009-11-18
Thanks again. I read through the guide and the comments on how to downgrade X. Sadly, the instructions do not work with karmic. It now looks like my only option is to do a fresh install of 8.10 :(

---

### Post by khelben1979 on 2009-11-18
> **buntuchimp said:**
> Thanks again. I read through the guide and the comments on how to downgrade X. Sadly, the instructions do not work with karmic. It now looks like my only option is to do a fresh install of 8.10 :(

Maybe it's time to upgrade to a better graphics card? Using older versions of software just because of a hardware limitation doesn't sound very fun.. In either way, using an open source driver from ATi will at least give you working graphics with Karmic, as I've understood.

---

### Post by buntuchimp on 2009-11-18
> **khelben1979 said:**
> Maybe it's time to upgrade to a better graphics card? Using older versions of software just because of a hardware limitation doesn't sound very fun.. In either way, using an open source driver from ATi will at least give you working graphics with Karmic, as I've understood.
Yeah, it doesn't sound very fun to downgrade. The more reading I do makes it seems like a new (or older) nvidia card may be the only other option. You make it sound like the card is too old to work properly and that is not the case - it is only about 3 years old. I believe I am already using the open source driver for it.

Is it possible that X-org has a newer version that has a fix for the ati driver? I have no idea where to start looking for that information. The Xorg site has a lot of info but I don't really understand most of it. This really suprises me as ATI must have around half the market share for video cards. Are half of the people excluded from using ubuntu 9?

---

### Post by Zoot7 on 2009-11-18
ATi have a large chunk of the video card market, but sadly Linux is hovering around 2/3% of the market, so they don't care really.
Having them support their fairly up to date cards as well as they do (given their history) is a wonder.

Anyway...
You could probably try booting off a livecd for Intrepid and downloading the required packages. Then force-installing them on Karmic.
But I don't hold much hope for that working though...

I'm inclined to agree with khelben1979, you'd be better off to get a newer card, preferably an nVidia one if you can.

---

### Post by buntuchimp on 2009-11-18
Ok, I got at least the 2d problems fixed. The issue was as posited in the OP: changes to the xorg.conf file. I didn't have a xorg.conf file from the initial install so I created a cropped down version containing just the device section.

Create the empty xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```paste in the following:
```

Section "Device"
 Identifier "ATI Radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic" "greedy"
 Option "AccelDFS" "true"
 Option "EnablePageFlip" "true"
 Option "EnableDepthMoves" "true"
EndSection
```save and restart computer.

This solved the cpu thrashing and delay every time a window was moved or opened. I hope this can hellp someone else with the same problem.

---

### Post by krustykrabs on 2010-03-08
"Maybe it's time to upgrade to a better graphics card? Using older versions of software just because of a hardware limitation doesn't sound very fun."

I too have an X1600 series card from ATI.  I was disappointed to find it wasn't supported by the latest ATI driver, then I was happy to find a legacy driver for it from ATI, then I was disappointed again to find that the driver didn't work with the latest Ubuntu.

Sure, it's not a screamin' demon, but it's a perfectly functional card that can easily handle anything I want to do in Ubuntu.  I played Far Cry 2 on the card in Windows and it performed acceptably, anything older than that runs great.  Since I don't plan on running Modern Warfare 2 in Ubuntu, I don't see the need to spend a couple hundred bucks on a new card.

Excellent performance on older hardware was Linux's bread and butter.  I think it's a serious mistake for xorg to not support the drivers that exist and are readily available from ATI.

Sure basic functionality is supported, but if you try to do anything more than surf the net you are met with sub par performance.  Even watching a normal quality avi video there are noticeable and recurrent glitches.  By contrast, in Windows it plays HD quality videos without missing a beat.

Back in the day people had to hack together video drivers from scratch because ATI didn't make Linux drivers.  There's just no excuse not to support hardware when the manufacturer provides the driver.  End rant.

---

### Post by Tikkyca on 2010-03-08
I have a problem too,when i try to record my desktop it laggs too much because of the ATI driver it doesn't do that on Nvidia drivers im trying to find a way to fix this.

---

