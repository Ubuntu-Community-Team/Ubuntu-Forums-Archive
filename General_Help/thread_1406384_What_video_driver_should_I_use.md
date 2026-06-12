---
title: "What video driver should I use???"
date: 2010-02-13
forum: General Help
---

### Post by ryanfx on 2010-02-13
Hey everyone,

I recently got a new laptop (NV5927U) and I can't get the graphics running correctly no matter what I do.  It has an intel based graphics chip but thats all I know.  Any help would be super appreciated getting this running.

9.10 displays a 100% black screen ( can't even get into virtual terminals)
9.04 displays the wrong resolution (1024x768 ), and using the vesa driver.  I'd be glad to give you any more output you may need


```

ryan@TehLaptop:~$ sudo lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0

```




```

ryan@TehLaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0044 (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Device 0046 (rev 12)
00:16.0 Communication controller: Intel Corporation Ibex Peak HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Ibex Peak 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation Ibex Peak Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation Device 1692 (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Device 2c62 (rev 02)
ff:00.1 Host bridge: Intel Corporation Device 2d01 (rev 02)
ff:02.0 Host bridge: Intel Corporation Device 2d10 (rev 02)
ff:02.1 Host bridge: Intel Corporation Device 2d11 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

```

```

ryan@TehLaptop:~$ cat /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by ryanfx on 2010-02-14
bump for some help?

Also, I found out the new beta Ubuntu works perfectly.. is there any way to copy its video configuration?  I'm confused why the beta recognizes it perfectly.

---

### Post by gradinaruvasile on 2010-02-14
Because the beta version has newer drivers in its kernel/X server.

---

### Post by ryanfx on 2010-02-14
> **gradinaruvasile said:**
> Because the beta version has newer drivers in its kernel/X server.

I see that it has loaded the i915, are you saying that the i915 in the beta is newer than the one in 9.10 / 9.04 and that's why it's working?

---

### Post by Ansikt on 2010-06-30
I'm having the exact same problem - running 9.04, same graphics card, similar computer (Gateway NV79) and I'm all stuck in 1024x768 even though I should have 1600x900.  Can't find any help anywhere, I actually made this username for the specific purpose of finding an answer to this problem, I've been searching for about an hour each day for a week.

Did you ever find a solution?  Does someone else know?

---

### Post by ryanfx on 2010-06-30
> **Ansikt said:**
> I'm having the exact same problem - running 9.04, same graphics card, similar computer (Gateway NV79) and I'm all stuck in 1024x768 even though I should have 1600x900.  Can't find any help anywhere, I actually made this username for the specific purpose of finding an answer to this problem, I've been searching for about an hour each day for a week.

Did you ever find a solution?  Does someone else know?


If you have the same graphics card, try upgrading to 10.04 - I am fairly confident it will fix your problems with the newer kernel.

---

### Post by davidmohammed on 2010-06-30
suggest download the 10.04 lucid desktop CD and use the option "try without installing" - see if you can see the desktop correctly (resolution, colour depth, 3D graphics etc).

If it does, suggest wipe your installation by installing 10.04 over the top.

---

### Post by Ansikt on 2010-06-30
Ach, my problem is that I'm actually running CrunchBang, which is built off Jaunty Jackalope sources, but isn't actually Ubuntu.  The next version of CrunchBang is currently in Alpha, and doesn't have 64bit yet, unless I want to try to build it.  I guess a new distro it is *sigh*

---

### Post by ryanfx on 2010-06-30
> **Ansikt said:**
> Ach, my problem is that I'm actually running CrunchBang, which is built off Jaunty Jackalope sources, but isn't actually Ubuntu.  The next version of CrunchBang is currently in Alpha, and doesn't have 64bit yet, unless I want to try to build it.  I guess a new distro it is *sigh*

Then if you are familiar with downloading and patching video drivers, get the driver out of 10.04 that I mentioned a while back and patch it into your current system.

---

