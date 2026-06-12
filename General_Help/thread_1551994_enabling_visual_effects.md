---
title: "enabling visual effects"
date: 2010-08-13
forum: General Help
---

### Post by luffy_chan_19 on 2010-08-13
i have searched the internet for a long time over this issue, and it is a bit aggravating. i have been trying to enable visual effects o my Ubuntu desktop pc, i had them enabled before and i restated my computer one day and wouldnt work after that. i have attempted to reinstall ubuntu several times sionce then, but havent been able to enable visual effects, i am running ubuntu 10.04 atm. 

my pc is a dell dimension 2400, upgraded slightly to 1GB of RAM, am utilizing 128mb shared video ram. leaving a link to my specs, hope someone can help me resolve the issue. 

system specs [http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4507-3118_7-30824846.html](http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4507-3118_7-30824846.html)

---

### Post by earthpigg on 2010-08-13
we will need vastly more details.

---

### Post by zolr on 2010-08-13
System > Preferences > Appearance > Visual Effects...?

---

### Post by luffy_chan_19 on 2010-08-13
aright so what is happening is i want to enable visual effects this is a semi fresh install of ubuntu 10.04 have configured a little but just added soem apps and astuff i use all ofthe timje, when i go to apearance and click enable visual effects it does the drivrer scan, and all that and says something like cannot enable desktop effects, before i would just install compiz fusion and it eould work, i would go to appearnce and "custom efects" would be selected. however i restarte my computer one daya and they just stopped working completely , sionce then i ahve repeatedly tried to reinstall ubuntu to see if trhat wa the probllenm. i have also attempted to go into the BIOs and up the usage of obnoard video card. specs should be there i just need to know whow i am suppused to know if my vidoe cvard is enabled and running and what i can use to enable it so i can utilise visual effects, the best suggestion i have gotten was to edit the xorg.conf but i dont know how to do that what i am supposed to add or whatnot. and how to make that work either. have attempted to run the hardware scan tiung and it said "no propitery drivers present" or whatever. u shoudldnt need much detail for enabling drivers. if this was a windowes system i could do it within 5 minutes but as it is not i am confused.

there is no device manager on ubuntu so idk what i am supposed t do...



also off topic but how do i do those text things below my posts? like yours earthpig....

---

### Post by Elfy on 2010-08-13
Run this from a terminal and post it 

```
lspci
```

Check in System - Admin - Hardware Drivers for available graphics drivers as well.

---

### Post by Elfy on 2010-08-13
Run this from a terminal and post it 

```
lspci
```

Check for driver in System - Admin - HArdware drivers

---

### Post by luffy_chan_19 on 2010-08-13
this is what i got 




00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)




and really how do you make it so that wwhen you write a post whatever it is under your post adds as well... im dub when it comes to forums

---

### Post by Elfy on 2010-08-13
[http://ubuntuforums.org/profile.php?do=editsignature](http://ubuntuforums.org/profile.php?do=editsignature) for > and really how do you make it so that wwhen you write a post whatever it is under your post adds as well... im dub when it comes to forums

---

### Post by JBAlaska on 2010-08-13
> **luffy_chan_19 said:**
> i have searched the internet for a long time over this issue, and it is a bit aggravating. i have been trying to enable visual effects o my Ubuntu desktop pc, **i had them enabled before and i restated my computer one day and wouldnt work after that.** i have attempted to reinstall ubuntu several times sionce then, but havent been able to enable visual effects, i am running ubuntu 10.04 atm. 

my pc is a dell dimension 2400, upgraded slightly to 1GB of RAM, am utilizing 128mb shared video ram. leaving a link to my specs, hope someone can help me resolve the issue. 

system specs [http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4507-3118_7-30824846.html](http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4507-3118_7-30824846.html)

Your driver is probably on the Compiz bliacklist, although I think the bug that put it there is now [Fixed](https://bugs.edge.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392)

To disable the blacklist, Do:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Disclaimer: It's been a while since I had a dell laptop with Intel graphics (Which is still working with compiz, as far as I know), and that command worked, but it may take some tuning for your .version.

---

### Post by luffy_chan_19 on 2010-08-13
> **JBAlaska said:**
> Your driver is probably on the Compiz bliacklist, although I think the bug that put it there is now [Fixed]("https://bugs.edge.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392")

To disable the blacklist, Do:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```Disclaimer: It's been a while since I had a dell laptop with Intel graphics (Which is still working with compiz, as far as I know), and that command worked, but it may take some tuning for your .version.
  

and this is supposed to do what exactly? didnt do anything for me....i went to enable "extra" visual effects and it did the same thing as b4 "cannot enable visual effects" or ewhatever it said.. tried to install conpiz again and check if that worked... and well it wont enable anything, not even do dektop wall, or desktop cube, wont rotate it wont do anythign and i had it all enabled b4 its annoying

---

### Post by JBAlaska on 2010-08-13
Every time you re-install Compiz, you will have to disable blacklist checks as above.

Did you restart X and then try to enable Compiz?

After disabling checks again, restart x or just reboot. 
Open a terminal and do:
```
compiz -- replace
``` and post any error messages.

If it works, enable it as normal on your next session.
.

---

### Post by luffy_chan_19 on 2010-08-13
and how do i "restart x"? and it did this 

Blacklisted PCI ID 8086:2562 detected

Launching fallback window manager

---

### Post by JBAlaska on 2010-08-13
Run this command again:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Then reboot, open a terminal and try ```
compiz -- replace
``` again.

if it still says: **Blacklisted PCI ID 8086:2562 detected**

You might have to create the file "compiz-manager" in **/etc/xdg/compiz/**

```
gksu gedit /etc/xdg/compiz/compiz-manager
```

And add the lines:
```
COMPIZ_NAME="compiz"
SKIP_CHECKS="yes"
```

Save and exit gedit, reboot and try enabling effects.

---

### Post by luffy_chan_19 on 2010-08-13
well tried that wouldnt save said di8rectory doesnt exist basically

---

