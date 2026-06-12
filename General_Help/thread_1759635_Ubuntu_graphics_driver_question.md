---
title: "Ubuntu: graphics driver question"
date: 2011-05-16
forum: General Help
---

### Post by airspoon on 2011-05-16
I just recently installed Ubuntu 11.04 on a Dell computer I aquired and am new to Linux all together. Before installing Ubuntu on the hard drive, I ran it from a thumb drive and everything seemed to work perfectly. So, I took the leap and installed it to the hard drive. The instillation seemed to go quickly and smoothly without a hitch.
 
However, after trying to log in, the computer would get stuck on a purple screen. After playing around with it, I noticed that there were other options to login to. I am able to login to the Ubuntu safe mode option and the Ubuntu classic option, but not the default "Ubuntu" option (with the nice graphical black task bar).
 
When I ran it from the thumb drive, I didn;t have a problem. It was only after installing it to the hard drive, so I figured it may be a problem with the driver.
 
So, I logged in to the "Ubuntu classic" mode and went to the "Control Center". After clicking on the "additional drivers" option, it says, "No proprietary drivers are in use on this system".
 
Then, I see a little green circle that says:
 
NVIDIA accelerated graphics driver (version 173) [Recommended]
 
On the bottom of the window, it has the same little green dot and says:
 
This driver is activated but not currently in use.
 
It says that I need to install this driver if I wish to use the unity desktop (I'm assuming that the unity desktop is the default desktop with the black taskbar in the screenshots on the Ubuntu website).
 
My question is, is this why I can only login to the Ubuntu classic desktop and "safe-mode", as opposed to the regular Ubuntu desktop? Do I need to install this driver or is it already installed and broken? If I do need to install this driver, how would I go about doing it?
 
Any and all help would be greatly appreciated. Thanks.

---

### Post by garvinrick4 on 2011-05-16
Open Synaptics: second one down I do believe. Right click mark for installation apply.

---

### Post by airspoon on 2011-05-16
Thanks, I just went to Synaptic and I see the nvidia-173 but the checkbox is shaded green. I believe this means it is already installed, right? Should I try to reinstall it? Thanks.

---

### Post by Quackers on 2011-05-16
Do you have a Nvidia 7300 by any chance?

---

### Post by airspoon on 2011-05-16
I have no idea what graphics card is in this computer. I literally just bought the computer for $50. It's a Dell Dimensions 8300 (P4 3ghz, 1gb RAM).

---

### Post by airspoon on 2011-05-16
If the "nvidia 173" driver is not in use, then which driver is? Under "System > Control Center> additional drivers", it says that the driver is activated but not in use. Then, in the Synaptic Package Manager, it says that the "nvidia 173" driver is installed.
 
So, if nvidia-173 is not in use, wouldn't that mean that some other driver has to be in use?

---

### Post by garvinrick4 on 2011-05-16
Run this in a terminal and copy and paste results here will give
users a look at your cards and drivers so can see what is going on.
```
lspci -k
```

---

### Post by airspoon on 2011-05-16
Thanks, here are the results:

dell:~$ lspci -k
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: agpgart-intel
    Kernel modules: i82875p_edac
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
    Kernel modules: shpchp
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: ata_piix
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Dell Device 0157
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
    Subsystem: nVidia Corporation Device 01b9
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nouveau, nvidiafb
02:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
    Subsystem: Dell Device 1000
    Kernel driver in use: serial
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
    Subsystem: Dell Device 0157
    Kernel driver in use: e100
    Kernel modules: e100

---

### Post by garvinrick4 on 2011-05-16
run this in a terminal and see if you can use 3d in unity or need 2d
```
/usr/lib/nux/unity_support_test -p 
```


driver should be in:
windows key and type Additional drivers and then enable it.

---

### Post by garvinrick4 on 2011-05-16
Here is a thread that sounds awful close to you in bugs at launchpad.
Hope it is working by now.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207)

---

### Post by machdohvah on 2011-05-16
The above discussion is just another example why I believe 11.04 is a step down and not a step forward in the evolution of Ubuntu. This why I would rather stick to version 10.10 for it is more reliable.

---

### Post by airspoon on 2011-05-16
Here are the results to the unity support test:

dell:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no



What exactly does this mean?

---

### Post by garvinrick4 on 2011-05-16
The only links I can come up with to get your 3D effects working with that card is this
same one.
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-10.04-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-10.04-desktop-nvidia-geforce-fx-5200)

If you can get it loaded users having lots of trouble with that card by the launchpad link I gave you. Instead of using simple compiz config. Use in Advanced Desktop effects settings in Ubuntu software center or:
```
sudo apt-get install compizconfig-settings-manager
```
and open by
```
ccsm
```
go to Ubuntu Unity plugin and make sure it is checked.

If you cannot get it running in 3d with that card as many cannot you will have to run in 2d
log-out click on your user name go to bottom and click on button and select 2D until this is
ironed out. Good luck to you
## Let us know your results.

---

### Post by garvinrick4 on 2011-05-16
> **machdohvah said:**
> The above discussion is just another example why I believe 11.04 is a step down and not a step forward in the evolution of Ubuntu. This why I would rather stick to version 10.10 for it is more reliable.
I think there is more of a long term goal to use gnome with compiz but they still have classic Gnome for users who wish to stick to the regular gnome interface as used in all flavors of the major linux players. I enjoy it and have been using Unity interface since the get-go, key commands fast and can get around easily and is now second nature. I am sure you have seen Gnome 3 which I looked at in Fedora 15 to stay on top of the yum's or Redhat cousins anyway, look rather familiar. (attached)
If we had all drivers produced for linux kernel and all upgraded as new kernels and new versions came out would be fantastic, with no restricted, but we do not. User share is just not there yet, one day hopefully it will and Linux will be on top. Remember when another Unix offshoot Mac was trying to play with big boys and only had the Desktop publishing users, Now 15 to 20 years later after just about folding a few time from then are on top of the heap. If you would have told me when I was just getting started in desktop publishing that one day 
Macintosh would be worth more dollar for dollar in stock times number of stocks outstanding then Windows ,would have laughed you out of the building.  Have to say there is a direction 
we are heading for a good reason, I am going to go with it. Good luck partner and have a nice day.

---

### Post by garvinrick4 on 2011-05-16
sorry gave wrong post here, wrong thread.

---

