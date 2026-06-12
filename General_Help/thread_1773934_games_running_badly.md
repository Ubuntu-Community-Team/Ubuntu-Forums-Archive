---
title: "games running badly"
date: 2011-06-02
forum: General Help
---

### Post by evilheart on 2011-06-02
i tried to download several games for lubuntu , but some of them are running badly , and slow the system down , although they are not very large one of them is just 100MB , other one was even much less than that.

i have pentium 4 , 512 ram . 128 MB built in video card  PC , is there any thing i can configure or download for that problem?

---

### Post by mike555 on 2011-06-02
" just 100 mb " , that is big .... you don't have a very fast computer, certainly not a "gaming" computer, added RAM would help , but still .

---

### Post by evilheart on 2011-06-03
> **mike555 said:**
> " just 100 mb " , that is big .... you don't have a very fast computer, certainly not a "gaming" computer, added RAM would help , but still .

i have much  larger games that run smoothly on windows , what is the difference with linux games ?

---

### Post by mastablasta on 2011-06-03
size of the game doesn't matter. 
 
it could be that your card doesn't have good linux driver support. what model is it? you might be able to install newer drivers that utilize the card better.
 
Also what game did you try that made a poor performance?

---

### Post by evilheart on 2011-06-03
> **mastablasta said:**
> size of the game doesn't matter. 
 
it could be that your card doesn't have good linux driver support. what model is it? you might be able to install newer drivers that utilize the card better.
 
Also what game did you try that made a poor performance?

super tuxkart and warsow , but i tried warsow on gnome not lubuntu , but nearly the same issue , lagging and chaning FPS ,

that's my  video card info , i don't know how it  works with lubuntu
```
-PCI Devices-
Host bridge		: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
VGA compatible controller		: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
Audio device		: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
PCI bridge		: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
PCI bridge		: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
ISA bridge		: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
IDE interface		: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 80 [Master])
SMBus		: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
Communication controller		: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
 
```

---

### Post by mastablasta on 2011-06-06
this is the graphics card - Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 
It's a crappy card and those games require a descent card to run as they use graphics acceleration which might not be enabled on your card. it also doesn't have some good driver support for current 
kernel i believe. i see many people reporting issues with these older intel chips.
 
Anyway you could try troubleshooting for issues by looking at this page: [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)
 
anyway you could try a driver upgrade though again i doubt it would have much effect: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
 
however even with the cheapest dedicated card you could buy all these games will work fine and the whole system would work much faster.

---

### Post by harryhamlin on 2011-06-06
Well..I don't think its a RAM problem coz I got 512MB RAM and believe me I use to play hell lot of games everyday without any problem...I'm sure that that the problem is with something else...

---

### Post by wildmanne39 on 2011-06-06
> **harryhamlin said:**
> Well..I don't think its a RAM problem coz I got 512MB RAM and believe me I use to play hell lot of games everyday without any problem...I'm sure that that the problem is with something else...HI, that really is a very low resource computer, I just worked on one for a family member it had xp and they wanted to play games from facebook and the cpu jumped to a 100 percent just opening the broswser, and the hard drive turned constantly because 512 mb just was not enough ram. That being said, what version of ubuntu are you using? and when you installed did you allow 2 gigs for swap? with your resources that is critical. You can run lubuntu or another desktop on ubuntu like xfce and it would be much easier on resources.

---

### Post by mastablasta on 2011-06-06
> **harryhamlin said:**
> Well..I don't think its a RAM problem coz I got 512MB RAM and believe me I use to play hell lot of games everyday without any problem...I'm sure that that the problem is with something else...
 
who said it was RAM? Lubuntu needs about 80-100MB to run and that leaves you about 280 MB to run the game. it's either the drivers or poor graphics card/chip in general.
 
> **wildmanne39 said:**
> HI, that really is a very low resource computer, I just worked on one for a family member it had xp and they wanted to play games from facebook and the cpu jumped to a 100 percent just opening the broswser, and the hard drive turned constantly because 512 mb just was not enough ram. That being said, what version of ubuntu are you using? and when you installed did you allow 2 gigs for swap? with your resources that is critical. You can run lubuntu or another desktop on ubuntu like xfce and it would be much easier on resources.
 
Please read a bit before you jump in and post. He uses **Lubuntu**!!
 
I am not sure what kind of computer your family member has, but if graphics chip is not dedicated then it will use processor power to handle graphics. while if you have a dedicated car then the processor on the card handles graphics leaving all else to be processed by main core.

---

### Post by wildmanne39 on 2011-06-06
> **mastablasta said:**
> who said it was RAM? Lubuntu needs about 80-100MB to run and that leaves you about 280 MB to run the game. it's either the drivers or poor graphics card/chip in general.
 

 
Please read a bit before you jump in and post. He uses **Lubuntu**!!
 
I am not sure what kind of computer your family member has, but if graphics chip is not dedicated then it will use processor power to handle graphics. while if you have a dedicated car then the processor on the card handles graphics leaving all else to be processed by main core.
Hi, I am sorry I did read it but I did not see that he was running Lubuntu, when he made the request for help all I saw was ubuntu I did not see the l. it was not capitalized and I missed it because my eye sight is not very good. This is what he said that made me think he was using ubuntu.
```
super tuxkart and warsow , but i tried warsow on gnome not lubuntu , but nearly the same issue , lagging and chaning FPS ,
that's my video card info , i don't know how it works with lubuntu
```Again I am sorry.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **evilheart said:**
> i tried to download several games for lubuntu , but some of them are running badly , and slow the system down , although they are not very large one of them is just 100MB , other one was even much less than that.

i have pentium 4 , 512 ram . 128 MB built in video card  PC , is there any thing i can configure or download for that problem?

Did you try install PlayOnLinux first before installing your game? 

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

---

