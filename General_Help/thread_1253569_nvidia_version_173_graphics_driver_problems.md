---
title: "nvidia version 173 graphics driver problems"
date: 2009-08-30
forum: General Help
---

### Post by tehwinrar on 2009-08-30
I've searched through a million of these stupid threads and people kept having similar problems to mine but I never found anything that actually fixed the problem. I was updating my driver and afterwards when I'd try to log into ubuntu the loading bar screen came up but the log in prompt did not and the screen stayed black. Previously I was able to log into safe mode and get to the desktop by using the option to fix xserver problems but this time I wasn't, it popped up some message that I don't get anymore and don't remember. Something about the sxerver being broken or something. I ignored it and followed some instructions I found that actually worked, kind of:

type sudo nano /etc/X11/xorg.conf
find the line that says Section "Screen"
insert a new line Option "UseDisplayDevice" "DFP"
save the file

Using that I was able to get to my desktop with relatively no problems so far except for a few. Also not really a problem but when I go into the hardware drivers menu and highlight the version 173 driver it says "a different version of this driver is in use." The only real problem I've found so far is that a few of my games will not play anymore: kubrick, teeworlds, and brutal chess(not sure if it ever worked actually, dowloaded it after updating the driver). I've actually had this problem before when trying to update my driver. This is really frustrating and it's the only problem I've had with ubuntu but it's extremely frustrating. I've had ubuntu for months and have never been able to update my stupid graphics driver without having problems. I would really appreciate any help.

---

### Post by P4man on 2009-08-30
what videocard do you have ?
If in doubt, post output of

```
lspci
```

---

### Post by tehwinrar on 2009-08-30
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)


I'm using an nVidia GeForce FX 5500 video card

---

### Post by NoaHall on 2009-08-30
The xserver is broken?
Try "sudo dpkg-reconfigure xserver-xorg"
and if that fails to solve it - "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by tehwinrar on 2009-08-31
> **NoaHall said:**
> The xserver is broken?
Try "sudo dpkg-reconfigure xserver-xorg"
and if that fails to solve it - "sudo dpkg-reconfigure -phigh xserver-xorg"

don't know if that made any difference but I tried it anyway, thank you.

Also when I try to go into the nvidia xserver settings a window with this message pops up:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I've found a million different answers on how to fix it but none I tried worked. Now when I run sudo nvidia-xconfig it doesn't say "command not found" or whatever it was saying so I'm assuming it's working but when I press ctrl+alt+backspace to restart the xserver it doesn't do anything and when I try to go back into the settings the same message pops up. If it has nothing to do with my other problem please don't worry about it, I'll figure it out eventually.

---

### Post by tehwinrar on 2009-08-31
not sure how to delete my posts so I changed this to this

---

### Post by tehwinrar on 2009-09-02
also I'm on 9.04 but i had this exact same problem with 8.10 and 8.04 and have never been able to resolve it.

---

### Post by fluffman86 on 2009-09-02
I've had Ubuntu download the wrong driver before.  Try this:
```

sudo apt-get remove --purge nvidia*
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install dontzap
sudo dontzap -d
(<ctrl + alt + backspace> will now restart the x server)
sudo apt-get install nvidia-glx-180
(yes, try 180 now, not 173)
sudo nvidia-xconfig
gksu nvidia-settings

```
You might want to write all this down as you may have to do it from a virtual terminal (ctrl + alt + f2).  If you get dropped to one, you can restart Gnome with
```
sudo /etc/init.d/gdm restart
```

And if all of that fails, try again, but replace the 180 driver with 173.

---

### Post by P4man on 2009-09-03
the OP has a geforce 5500, that is not supported by the 180 glx drivers.
He needs the 173 driver, but I wonder if that supports the latest xorg as I see quite a lot of posts with problems related to teh 173 and jaunty :s

---

### Post by tehwinrar on 2009-09-05
I did what fluffman said to do, first with the 173 driver then with the 180 driver and then with the 96 driver and none of them worked. But something weird happened to me at 2 am this morning and i was tired so i forgot to write down exactly what it said but when i started up ubuntu instead of loading up a window popped up and said there was something wrong with my graphics settings or something and so i reset them to default and it saved my previous settings and loaded the default ones. I'm still having the same problem though. I found out there's someone on my floor who runs linux, not sure if it's ubuntu but i'm gonna see if he can help too.

---

