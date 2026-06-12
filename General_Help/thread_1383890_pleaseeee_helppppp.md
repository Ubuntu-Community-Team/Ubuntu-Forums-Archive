---
title: "pleaseeee helppppp"
date: 2010-01-17
forum: General Help
---

### Post by lucas1136 on 2010-01-17
pleaseeee help ive got ubuntu(google os) and i have tried alotttt of times trying to make my internet work ive tried to get ndiswrapper but im not sure how to get and install it can someone please help it would be greatly apprieciated!

---

### Post by Mr Nemo on 2010-01-17
If I understood that correctly you installed Ubuntu (which is not a google OS) and you're having trouble getting your internet to work. A little more information about your system and problem would help.

---

### Post by lucas1136 on 2010-01-17
sorry yeah thanks ive got a compac and im not sure what graphics card it is but i searched everywhere and its telling me to get this ndiswrapper

---

### Post by lucas1136 on 2010-01-17
a compac v5000

---

### Post by ubudog on 2010-01-17
The easiest thing to do is to get a usb wireless adapter.  Make sure you get one that works "Out of the box" on Ubuntu.

---

### Post by lucas1136 on 2010-01-17
oh god im an idiot im saying all the wrong things ive got a compac v5000 im not sure what wireless card it is but everywhere i search people are telling me that i need to get ndiswrapper sorry

---

### Post by jamesisin on 2010-01-17
Let us begin simply.  How do you know you don't have an Internet connection?  Do you get some errors which you could tell us about, for instance?

---

### Post by Mr Nemo on 2010-01-17
You should go to Synaptic by clicking on System --> Administration --> Synaptic Package Manager and then type in ndiswrapper and install the files that pop up. I see three that show up, but it could be more for you. Installing one should install all that are required. I suggest installing ndisgtk and following it from there. Report back.

*jamesisin probably knows more than me*

---

### Post by lucas1136 on 2010-01-17
im on a diferent computer and i want the other 1 to work and thanks ill try that

---

### Post by lucas1136 on 2010-01-17
thanks but that didnt work nothing came up for both

---

### Post by Xog on 2010-01-17
pop in your ubuntu installation CD. in the CD should be a folder called "pool" then open "main" then a list of folders in alphabetical order will show. open "n" and then open the first folder and run the .deb file and install. after that's done click Back and open the 2nd folder. run both of those .deb files 1 at a time and install each.

doing this will install ndisGTK and ndiswrapper.

I'm waiting on instructions on what to do next. I'm in the same boat as you.

---

### Post by Mr Nemo on 2010-01-17
What specifically didn't work? Also read jamesisin's post.

---

### Post by lucas1136 on 2010-01-17
sory jamesisin i didnt read ur proporly question i try to connect to my dads internet connection but it dosent work and hes got windows so he cant help me because he knows nothing about linux but he says it might be because of the wireless card that dosent work with linux

---

### Post by lucas1136 on 2010-01-17
thanks xog ill wait

---

### Post by lucas1136 on 2010-01-17
how do i get to java and ubuntu place

---

### Post by jamesisin on 2010-01-17
Ok, you try to connect to a local wireless network and "it doesn't work".

Do you get some errors?  What exactly happens?  How can you tell it's not working?

---

### Post by warfacegod on 2010-01-17
First, go to System> Admin.> Hardware Drivers and select and activate the recommended wireless driver.

If that doesn't work or there isn't one then do this.

Go to Applications> Accessories> Terminal and enter:

```
lspci
```

Hit enter. It will show you something like this:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
02:04.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:04.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:06.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```

Note the second line that says Ethernet controller. Mine says Atheros Comm... AR5211... The AR5211 is my wireless card chipset. Find yours in the output the Terminal created and go here to see if your wireless card is supported:

[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

However, if your card isn't supported, that doesn't mean that you can't get it to work.

---

### Post by lucas1136 on 2010-01-17
i dont think mine is supported

---

