---
title: "warning about vmware-player and possible fix"
date: 2006-06-01
forum: General Help
---

### Post by ubuntu_demon on 2006-06-01
Hi,

This is a warning about vmware-player and some information about a fix if it happens to you.

Today I've installed vmware-player. (sudo apt-get install vmware-player)

After a reboot my network didn't work. I'm almost 100% sure vmware-player is the cause because the problem is related to restricted-modules and networking and I haven't done anything else which might have caused this.

After a bit of thinking, searching the forums and trying some things I was able to come up with a solution.

This is what I have done to fix it :

backup your network configuration :
$sudo cp /etc/network/interfaces /etc/network/interfaces.bak

$ sudo apt-get remove vmware-player
$ sudo dpkg-reconfigure linux-image-`uname -r`

backup your network configuration for a second time. Since removing vmware might have altered it:
$sudo cp /etc/network/interfaces /etc/network/interfaces.bak2

edit your network configuration to make sure it is how it should be :
$sudo gedit /etc/network/interfaces
Or alternatively system->networking->click on the properties of your networkcards (for example eth0) and make sure everything is alright. If you have no idea you should probably leave the settings as they are or set it to dhcp.

Now I could reboot and have internet again :

$ sudo reboot

But I couldn't get into X because for some reason "nvidia" couldn't be modprobed. (I have a nvidia videocard so I don't know the exact steps for ATI)

[I]A temporary fix to get into X.

Edit your /etc/X11/xorg.conf 

$sudo pico /etc/X11/xorg.conf

and change nvidia to nv in this part :
```

Section "Device"
        Identifier      "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

```

and do :
$sudo init 1
$init 2
or a reboot

End of temporary fix to get into X.
[/I]
Only do the following steps if your internet works again otherwise you might have to install the packages from the cd.

$ sudo apt-get remove nvidia-glx
$ sudo apt-get remove nvidia-kernel-common
$ sudo apt-get install nvidia-glx 
$ sudo apt-get install linux-686 (or whichever kernel you are running)
$ sudo init 1
$ sudo modprobe nvidia
$ init 2

And now everything is fixed and working fine again :).

I think it only happens in certain cases. Maybe it's related to the motherboard or other hardware , maybe not. 

Here's my $lspci :
```

0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
0000:02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)

```

---

### Post by ubuntu_demon on 2006-06-02
here are related threads :
[http://www.ubuntuforums.org/showthread.php?t=185715](http://www.ubuntuforums.org/showthread.php?t=185715)
[http://www.ubuntuforums.org/showthread.php?t=186276](http://www.ubuntuforums.org/showthread.php?t=186276)

---

