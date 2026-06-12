---
title: "Onboard vga resolution"
date: 2010-10-21
forum: General Help
---

### Post by ammoun on 2010-10-21
Hi,

I struggled to install 10.10 as the screen resolution was not appropriate.

6.04 and 8.04 are fine
10.04 and 10.10 aren't 

Motherboard is PC Chips p25g v1.0a, VGA VIA onboard

The screen is shown as Unknown, and I can only get the desktop in (Safe Mode), else the login windows just reappears.

Tell me if you need to look at any file,

I don't have xorg.conf in /etc/X11, but have default-display-manager with 1 line: 
/usr/sbin/gdm

Thanks

---

### Post by ammoun on 2010-11-23
sudo dpkg-reconfigure -phigh xserver-xorg  doesn't show anything.

lshw:

  *-display UNCLAIMED
       description: VGA compatible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: memory:f4000000-f7ffffff memory:f8000000-f8ffffff
memory:f9000000-f900ffff


Please give any hints to follow...
Thanks

---

### Post by ammoun on 2010-11-24
If you had same problem, where would you look at?

---

### Post by dcstar on 2010-11-25
> **ammoun said:**
> Hi,

I struggled to install 10.10 as the screen resolution was not appropriate.

6.04 and 8.04 are fine
10.04 and 10.10 aren't 

Motherboard is PC Chips p25g v1.0a, VGA VIA onboard
........

No longer supported according to a comment down the end of this:

[http://deviceguru.com/previewing-and-tweaking-ubuntu-maverick/](http://deviceguru.com/previewing-and-tweaking-ubuntu-maverick/)

---

### Post by ammoun on 2011-01-04
> **dcstar said:**
> No longer supported according to a comment down the end of this:

[http://deviceguru.com/previewing-and-tweaking-ubuntu-maverick/](http://deviceguru.com/previewing-and-tweaking-ubuntu-maverick/)

I managed to work around xorg with few tweaks in conf file but frankly the PC is lagging more than ever.

Thank you so much David!

---

