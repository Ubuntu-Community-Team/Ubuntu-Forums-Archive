---
title: "HDMI output cut off at the edge"
date: 2010-03-17
forum: General Help
---

### Post by sokam on 2010-03-17
I have a on-board video card (ATI Radeon HD4200) that capable to output HDMI as well as VGA.  I connected both into my TV (which also have VGA input as well as HDMI).  

Here is the weird thing:  

IF I reboot my computer (9.10 64bit) with my TV set to display HDMI, then after I login at my workspace, my HDMI display got cut off at the edge!  BUT my VGA display correctly when I switch to it on my TV.

HOWEVER, IF I reboot my computer with my TV set to display VGA, then after I login at my workspace, my VGA display correctly AND my HDMI display correctly.

What's the deal here?  I am trying to use only HDMI connection and eliminate the VGA as well as the analog audio wire (which the HDMI audio is another big problem but for another post).

---

### Post by sokam on 2010-03-22
No one had similar situation?

---

### Post by sokam on 2010-03-24
No one have similar situation???  REALLY!!

---

### Post by vertago1 on 2010-03-24
probably because not many people use HDMI yet, I use DVI myself. You might paste your Xorg config on here so we can take a look at it.

---

### Post by sokam on 2010-03-30
I just did a fresh install and re-installed the ATI restricted driver.  Tested with the same condition and have the same problem. -- Both HDMI and VGA is plug into the computer, when I have the TV at HDMI and reboot the computer, the computer cut off the edge of the screen in HDMI but not in VGA.  When I have the TV at VGA and reboot the computer, both HDMI and VGA display the whole view.

Here is my xorg.conf.

> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


Something is not correct when Ubuntu is detecting HDMI connection when it boot.

---

### Post by vertago1 on 2010-03-30
From your xorg file it looks like the screens are not setup. I know this isn't a requirement for the newer versions of xorg but it means you didn't use amdcccle to configure the display. You might want to try using amd's configuration tool to set the monitor positions and modes and then save it and see if it makes any difference. To do this you need to run:

[COLOR="Red"]sudo amdccle[/COLOR] Edit: This was wrong it is supposed to be:

sudo amdcccle

---

### Post by sokam on 2010-04-01
> 
$sudo amdccle
sudo: amdccle: command not found

$ sudo apt-get install amdccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amdccle


Any idea?

---

### Post by vertago1 on 2010-04-01
> **sokam said:**
> Any idea?

Sorry I had a typo there are 3 'c's:

amdcccle

There is a package fglrx-amdcccle but if you installed the proprietary drivers from the ati website do not use this package.

---

### Post by sokam on 2010-04-05
> **vertago1 said:**
> Sorry I had a typo there are 3 'c's:

amdcccle

There is a package fglrx-amdcccle but if you installed the proprietary drivers from the ati website do not use this package.

I already installed the proprietary driver from "Hardware Drivers" when I did a fresh install recently.  Can I use what you said above?

I am a bit hesitated because the reason I did a fresh install recently was that I downloaded the driver from ATI website & somehow screw up the display completely when I try to get the HDMI audio working.  Currently the HDMI audio still not working but I can live without it using multi-channel into my stereo.  

I wish I can only need HDMI to connect to the computer for both audio AND video without having such problems AND when I boot it thru XP, the display and sound both work on HDMI.  AFTER ALL, I did pay for the motherboard for all these functions that right now I am limited with Ubuntu.  

BTW, my motherboard is MSI 785GM-E51 model# MS-7596.  IF anyone have the same mobo and work fine with HDMI sound & display, please show me what you did exactly.

---

### Post by vertago1 on 2010-04-05
> **sokam said:**
> I already installed the proprietary driver from "Hardware Drivers" when I did a fresh install recently.  Can I use what you said above?

If you got the proprietary driver installed, and somewhat working you should be able to install the package fglrx-amdcccle from the package manager without having to worry about messing up your system.

I am using the Kubuntu 10.04LTS beta1 on my desktop. Some of the package names changed and they have a newer, better version of catalyst available. I don't recommend that you upgrade to the beta but I know that there should be a package for amdcccle if you don't already have the command available.

Pretty much what it does is open up a graphics based configuration like the one you have in windows for configuring the features of the ATI driver. You should be able to run amdcccle without it changing your system.

---

### Post by 1Tanuki on 2010-05-08
> **vertago1 said:**
> I am using the Kubuntu 10.04LTS beta1 on my desktop. Some of the package names changed and they have a newer, better version of catalyst available. I don't recommend that you upgrade to the beta but I know that there should be a package for amdcccle if you don't already have the command available.

Pretty much what it does is open up a graphics based configuration like the one you have in windows for configuring the features of the ATI driver. You should be able to run amdcccle without it changing your system.

ive had this exact same problem for several months this is the first case ive found, so i hope you can help me... i am running the kubuntu 10.04 beta1 on my desktop aswell.. its awesome.. and i was hoping it would fix my problem with the edge of the screen being cut off.. but it didnt, i have an on board GeForce 7100 / nForce 630i with both VGA and HDMI, i dont currently have wondows, cuz i hate microsoft, it took me a long time to kill vista, but i finally did.. anyway..amdcccle is for configuring the features of the ATI driver, but i have nvidia, so do i use the same?, i installed the package fglrx-amdcccle, but when i type it in to the terminal it says command not found.. so i assume im using the wrong driver... but i dont know which one to use.. i thought they would have fixed this problem with the 10.04...any help would be apprecated

thanks in advance :)
Tanuki

---

### Post by vertago1 on 2010-05-09
> **1Tanuki said:**
> ive had this exact same problem for several months this is the first case ive found, so i hope you can help me... i am running the kubuntu 10.04 beta1 on my desktop aswell.. its awesome.. and i was hoping it would fix my problem with the edge of the screen being cut off.. but it didnt, i have an on board GeForce 7100 / nForce 630i with both VGA and HDMI, i dont currently have wondows, cuz i hate microsoft, it took me a long time to kill vista, but i finally did.. anyway..amdcccle is for configuring the features of the ATI driver, but i have nvidia, so do i use the same?, i installed the package fglrx-amdcccle, but when i type it in to the terminal it says command not found.. so i assume im using the wrong driver... but i dont know which one to use.. i thought they would have fixed this problem with the 10.04...any help would be apprecated

thanks in advance :)
Tanuki

The command for nvidia is:

sudo nvidia-settings

---

### Post by 1Tanuki on 2010-05-11
> **vertago1 said:**
> The command for nvidia is:

sudo nvidia-settings
thanks for your quick reply... this command just opens the nvidia x server settings, which dont let me adjust where the edge of the screen is... so its still cut off...

---

### Post by sokam on 2010-09-02
I am still hoping to get my HDMI sound and display work perfectly.  Anyone else have any idea? I re-installed with 10.04 but not helping at all.  A second reason I want to use HDMI display is that my VGA display show a small offset ghost shadow that HDMI don't have.

---

### Post by Black.Ghost on 2011-02-10
> **sokam said:**
> I am still hoping to get my HDMI sound and display work perfectly.  Anyone else have any idea? I re-installed with 10.04 but not helping at all.  A second reason I want to use HDMI display is that my VGA display show a small offset ghost shadow that HDMI don't have.


I have smaller proplem. I fax it from ATi : (Catalyst Control Center)

System > Preferences > Catalyst Control Center

and from side menu choose Display Manager > DTV 

Choose Adjustment from top menu:

Put Scaling Options until it fax the edge : I put in 0 for my Sony Bravia TV and it works very well.

---

