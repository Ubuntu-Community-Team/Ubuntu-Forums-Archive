---
title: "Ubuntu 9.10 Resolution"
date: 2009-10-23
forum: General Help
---

### Post by AxlDLuffy on 2009-10-23
I had the same problem when I installed Ubuntu 9.04 so I thought maybe the problem is solved if I install Ubuntu 9.10 RC. It's not! :) 

There's the problem: 

My monitor is Samsung Syncmaster P2370, it is 23 inches and has a resolution of 1920x1080. But the max resolution I have in Ubuntu is the streched 1600x1400. I've activated the ATI driver but I have no 1920x1080 res. I tried this guide: [http://www.ngohaibac.com/how-to-install-ati-graphic-driver-for-ubuntu-904/](http://www.ngohaibac.com/how-to-install-ati-graphic-driver-for-ubuntu-904/) but still no progress. I suspect that I have to install the Monitor driver cause I remember having the same problem in windows and after I installed the Monitor driver (found here: [http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05024700&prd_mdl_cd=LS23EFHKFV%2fZA&prd_mdl_name=P2370](http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05024700&prd_mdl_cd=LS23EFHKFV%2fZA&prd_mdl_name=P2370) ) I had the 1920x1080 option. The thing is the there's no Linux driver as you can see.

If that's the case, what can I do about that? Can I force the 1920x1080 resolution? 

I'm a newbie so if I have to use command line, please be ultra comprehensive.

Excuse my english!

Thank you very much!__

---

### Post by QIII on 2009-10-23
The new 9.10 ATI driver that supports Karmic is not yet released for public consumption by ATI.  It is, however, included with Karmic.

ATI was tired of being at the back of the pack and looking at nVidia's back side mile after mile.  They jumped through hoops and provided a pre-release of their 9.10 driver, completely skipping 9.09, to have it included specifically, and only, in Karmic (too bad for all the other distros!)

Actually, despite the instructions you used, you should have installed the restricted driver using the restricted driver installation, since that is the only place it exists.

Then, using the Catalyst Control Center (9.10), you may be able to get the proper resolution.

What you have right now is probably the 9.08 or 9.09 version.

I'm not sure how much you would muck things up by trying to uninstall and reinstall the correct one.

---

### Post by AxlDLuffy on 2009-10-23
Unfortunatelly, Catalyst Control Center doesn't grand me the 1920x1080 I want... :/ I have the 9.10 CCC. What should I do? 

Thanks for the quick response. :)

---

### Post by QIII on 2009-10-23
Not at any of my Ubuntu machines right now, but it seems that at some point I was able to use CCC to force a choice for unlisted resolutions.

Maybe you have to use gksudo to open it?  I don't remember off the top of my head.

---

### Post by AxlDLuffy on 2009-10-23
It's true that CCC in Windows forces the requested resolution. But in Ubuntu I don't have that option. Still the max resolution is 1600x1400. 

How do I use ***gksudo***? Sorry for the newbie question but I'm having my first steps in this magin world... :P

---

### Post by QIII on 2009-10-23
I'm going to test something when I get home before I tell you to do it, but I'll let you know how to get into CCC with elevated privileges -- if I find that you can do what I think you can.

---

### Post by fragos on 2009-10-23
The ATI driver you're using determines what resolutions it will support. Apparently the ATI 9.10 driver will solve your problem. The only way I recommend installing video drivers is with the Hardware Drivers preferences. I'm an Nvidia user and in that case the Hardware Driver function tells me what video driver versions are available that support my card and I can select from those. I'd expect you have a similar situation with the ATI drivers.

---

### Post by AxlDLuffy on 2009-10-24
The problem is that I have the 9.10 ATI driver but still not the 1920x1080 option.
I installed openSuSE 11.1 and Linux Mint to check if the problem is solved that way but still nothing. 

In what other way can I approche the problem?

Thank you.

---

### Post by fragos on 2009-10-24
The driver is your limiting factor. No doubt that problem will be fixed in the future as HD 1080 monitors become more prevalent. For now I've no other suggestions. [http://ubuntuforums.org/showthread.php?t=542381](http://ubuntuforums.org/showthread.php?t=542381) may be helpful.

---

### Post by AxlDLuffy on 2009-10-25
Ok , thank you anyway.. :)

---

### Post by c_martini on 2009-10-26
I have a similar problem as well with an ATI Mobility Radeon HD 3470 (laptop: Asus M51se). The laptop lcd and second monitor connected to dfp1. Both are mirrored and are sharing the same resolution in error. Both need to be at their native resolutions (lcd at 1440x900 and dfp1 at 1650x1080) and have the desktop extend from the first to the second. I have read that the Catalyst Control Center app can manage this as the monitor settings within KDE are buggy and do not work in this scenario.  Really what I need to know is how to launch the Catalyst Control Center. I cannot find this anywhere in any of the application menus. Is there a terminal command to launch this? I am assuming this catalyst control center was installed during the restricted driver installation prompt after I installed the system yesterday (Kubuntu Karmic 9.10 rc). 

Would the control center have been installed or not?

How would I launch this?

---

### Post by AxlDLuffy on 2009-10-30
Ok , after I installed Ubuntu 9.10 Karmic Koala some of the facts have changed but the problem remains. So I'm going to describe the new facts in a desperate way to fix this.

My system specs are:

[I][SIZE=1][COLOR=Blue]CPU:[/COLOR] AMD Phenom II 965 3.4GHz Black Edtion
[COLOR=Blue]MoBo:[/COLOR] ASUS Crosshair III Formula
[COLOR=Blue]RAM:[/COLOR] Corsair Dominator DDR3 3X2GB 1600MHz
[COLOR=Blue]GPU:[/COLOR] Sapphire Radeon Vapor-X HD 4890 2GB GDDR5
[COLOR=Blue]HDD1:[/COLOR] WD 500GB Black Caviar 
[COLOR=Blue]HDD2:[/COLOR] WD 1TB Green Caviar
[COLOR=Blue]Case: [/COLOR] CoolerMaster Haf 932 Black Case 
[COLOR=Blue]PSU:[/COLOR] Crosshair CMPSU-650TXEU 650W
[COLOR=Blue]Monitor:[/COLOR] Samsung Syncmaster P2370

And right now I'm using Ubuntu 9.10 64bit.

Having Ubuntu 9.04, openSuSe 11.1 and Linux Mint, and after the intallation of  the Ati drivers (using the Hardware Manager either the manual installation) I was not able to setup a resolution of 1920x1080 in my monitor. Also for a reason unknown to me (and everyone else I asked) when I typed in the terminal "aticonfig" or "aticonfig --initial) the response was: "aticonfig: no supported adapters detected".
Not to mention the watermark in the down-left corner of my screen saying: "AMD Not supported hardware"

I just installed Ubuntu 9.10 Karmic Koala and what is changed is that the command "aticonfig" works!!! But the command "aticonfig --initial" does NOT!!! (Really, what the &@$%???)
Also I don't get the annoying watermark anymore.

After I installed the FGLRX driver though the Hardware Drivers section my xornf.conf looks like this:

[/SIZE][/I]```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection



```[I][SIZE=1]

Also I have to say that I have the same problem in Windows, only the problem is fixed when I install the Monitor Driver from Samsung (found here: [http://www.samsung.com/gr/support/download/supportDown.do?type=monitor&type_cd=05020000&subtype=Others&subtype_cd=others&model_nm=P2370&mType=DR&vType=L&prd_ia_cd=05023000&disp_nm=P2370](http://www.samsung.com/gr/support/download/supportDown.do?type=monitor&type_cd=05020000&subtype=Others&subtype_cd=others&model_nm=P2370&mType=DR&vType=L&prd_ia_cd=05023000&disp_nm=P2370)). Before the installation of the monitor driver, the max reso I can have is again 1600x1200 but after that I can have 1920x1080. So I suppose that I have to force the monitor the reso I want somehow...

please, PLEASE, help deal with this really frustrating problem. Excuse my english and again thank you in advance... 
[/SIZE][/I]

---

