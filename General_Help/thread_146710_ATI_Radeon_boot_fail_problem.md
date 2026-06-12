---
title: "ATI Radeon boot fail problem"
date: 2006-03-18
forum: General Help
---

### Post by NutrOn on 2006-03-18
I have just installed a ATI radeon 9500 into an AGP slot, I previously had installed an Nvidia and had downloaded the drivers. Now my startup fails due to Xserver not recognising display. log is not usefull, message on startup is now "Nvidia taint". Do I have to reinstall my system? I only have a minimal boot disk with limited software and I am not "expert". Thanks for any help. 
"NutrOn"

---

### Post by Mustard on 2006-03-18
A temporary workaround to get a GUI again is to reconfigure xorg.conf to use the 'vesa' drivers, until such a time as you uninstall your nvidia drivers and install the ATI drivers.

Step 1. Is normally to shut down GDM, but yours is not running, so I guess thats redundant. Just for those who might one day read this and want to reconfigure their xorg.conf using this method, I'll include it.

```
sudo /etc/init.d/gdm stop
```

Step 2. To reconfigure xorg..

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the default answers when the dialog starts, when it comes to choosing the video drivers, choose 'vesa'.  When you complete the dialog, it will make a backup of your old xorg.conf and name it according to the date and time it was changed.  Then it will create a new xorg.conf using the answers you gave in the dialog.

Step 3. Start X/GDM

Try either of these commands to get X to start again...

```
startx
```

or 

```
sudo /etc/init.d/gdm restart
```

You should have a GDM login screen now. *fingers crossed*

Now you can find information on uninstalling nvidia drivers and installing ATI drivers.  Details for uninstalling the nvidia drivers will really depend on what method you used to install them.  Instructions for installing ATI drivers are in the how to, tips and tricks section of this forum.

---

### Post by NutrOn on 2006-03-18
Thanks, I'll give it a wirl.
The errors were (if any one else reponds) no devices detected and fatal sever error no screens found, but it DOES find the NVIDIA even though the hardware is gone, seems like a detection problem where there is no work around at boot to autodetect the new hardware or perhaps having drivers available on the boot disk for ATI and a post hardware install or detect solution at boot or from bootdisk. Finding a lot of people with problems with ATI, especially in recent posts.
Thanks again.
NutrOn

---

### Post by bluevoodoo1 on 2006-03-18
[QUOTE=NutrOn]Thanks, I'll give it a wirl.
The errors were (if any one else reponds) no devices detected and fatal sever error no screens found, but it DOES find the NVIDIA even though the hardware is gone, seems like a detection problem where there is no work around at boot to autodetect the new hardware or perhaps having drivers available on the boot disk for ATI and a post hardware install or detect solution at boot or from bootdisk. Finding a lot of people with problems with ATI, especially in recent posts.
Thanks again.
NutrOn[/QUOTE]

I couldn't get my computer to run X or boot a LiveCD after I upgraded to a video card rather than using the onboard video. Here's what I did to fix that. If your problem is something to do with X not finding the correct video card, this might help... 

Back at the command line check your video bus location with...
```
lspci
```

Make note of its number, perhaps with pen/paper. Here's an example... the line in red is what Ubuntu recognizes as my onboard video at 01:05.0, but my monitor is now plugged into my nvidia card 02:09.0 so in the "dpkg-reconfigure" dialog I had to type in the new location to 02:09.0.

```

bluevoodoo1@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5833 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
[COLOR="Red"]0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5834[/COLOR]
0000:02:08.0 Ethernet controller: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller (rev 40)
[COLOR="DarkGreen"]0000:02:09.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)[/COLOR]
0000:02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:0c.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 02)
0000:02:0c.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
```

Run "sudo dpkg-reconfigure xserver-xorg" again and when it asks for the location of your video bus make sure you type the correct one in (the one you wrote down). When it finishes. Ctrl+Alt+F1 (if you're not already there). Login, and...

```
sudo /etc/init.d/gdm restart
```

should *hopefully *get you up and running. 

A couple of screens from dpkg-reconfigure are attached to show what I mean.

EDIT: And as the first post suggested, use the "vesa" driver to get you on your feet, if all else doesn't work.

---

