---
title: "API Mismatch NVIDIA DRIVERS NO GUI"
date: 2011-03-21
forum: General Help
---

### Post by YfoMp5QBh2 on 2011-03-21
Hi All,

I have made a screw up of my NVIDIA drivers and I'm not sure how to put it right. I stupidly downloaded the NVIDIA drivers for my Geforce 8400 GS, and tried to install them manually. I didnt backup my xorg.conf file before I did this either (I know!).

On startup I get the following error message: ERROR API MISMATCH using kernel module 260.19.06 but has 260.19.44 (this is the one I installed).

Have checked the forums already and I either have to downgrade my drivers or update the kernel. I have posted below  the Nvidia bug report and the contents of my xorg.conf file. How can I sort this out?

XORG.CONF - [http://pastebin.com/SugK0U1h](http://pastebin.com/SugK0U1h)
NVIDIA BUG REPORT - [http://pastebin.com/WEPVCeYu](http://pastebin.com/WEPVCeYu)


Thanks everyone,
SPADGE_2356

---

### Post by t.rei on 2011-03-21
Try the newest beta drivers (they work with natty - if you installed that - and xorg 1.10) 

[ftp://download.nvidia.com/XFree86/Linux-x86/270.30/](ftp://download.nvidia.com/XFree86/Linux-x86/270.30/)

---

### Post by YfoMp5QBh2 on 2011-03-21
> **t.rei said:**
> Try the newest beta drivers[ ftp://download.nvidia.com/XFree86/Linux-x86/270.30/]("ftp://download.nvidia.com/XFree86/Linux-x86/270.30/")

Thanks t.rei, but this won't cure the problem! It seems to be complaining about the kernal being changed from 260.19.06 to 260.19.44. I tried your suggestion anyway and now it complains that the Kernal 260.19.06 doesnt match with the new one I installed which is 270.30 :(

I think the solution might be just to re-install 260.19.06, but I havent been able to find it on NVIDIA's site.

---

### Post by YfoMp5QBh2 on 2011-03-21
OK everyone, my bad. Managed to re-install the old drivers by going to synaptic package manager and re-installing the Kernal modules and drivers completely!

Problem solved!

---

### Post by gsimpson on 2011-04-01
Ok. I am stuck at the command line with no GUI with API mismatch 260.19.29 vs 260.19.44

How did you get to synaptic package manager and re-install the Kernel modules?

---

### Post by fudoki on 2011-04-01
Having had this sort of thing happen numerous times before with Ubuntu, I kept my 173.xxx drivers - now, on any update, the system wants to nuke my Nvidia drivers and leave me with a command line box.  Kind of defeats the purpose of a 2x4 core AMD64 DAW/Graphics workstation...  It would really be great if this could be fixed, or an announcement made that Nvidia is no longer supported - just to get on with life...

---

### Post by t.rei on 2011-04-01
Ok, here is what I myself do, every time the nvidia driver gets borked by some upgrade of the kernel or xserver and modules:

Ctrl+Alt+F2 to go to the text console.
login
```
sudo service gdm stop
sudo sh /home/myname/Software/nv/NVIDIA-Linux-[COLOR=DarkRed]x86[/COLOR]-270.30.run -a -q -s
```
wait for it to do it's thing (no questions, proceed always, no gui as parameter options)
```
sudo service gdm start ; logout
```

As you can see, I am running an [COLOR=DarkRed]x86[/COLOR] install, not anything 'fancy' like 64 bit or anything. Compatibility reasons for gaming and such when installing a really long time ago - ever sind then it survived the upgrades. ;)

My xorg.conf is rather minimalistic (I run a laptop+second screen):
```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor            "Configured Monitor"
    Device            "ConfiguredVideoDevice"
    Option             "AddARGBGLXVisuals" "True"
    Option        "TwinView" "1"
    Option        "TwinViewXineramaInfoOrder" "DFP-0"
    Option        "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1920+0"
    DefaultDepth    24
EndSection

Section "Module"
    Load                "glx"
EndSection

Section "Device"
    Identifier    "ConfiguredVideoDevice"
    Driver            "nvidia"
    Option            "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option "IgnoreABI"
EndSection

```

---

