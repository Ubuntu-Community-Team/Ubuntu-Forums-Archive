---
title: "Help I can't change my resolution"
date: 2009-10-15
forum: General Help
---

### Post by Sanjuro82 on 2009-10-15
This is very annoying.  I just installed 9.10 beta on a new Dell computer.  I started from scratch and did a fresh install.  Everything went smoothly.  After the install and reboot, i tried to change my resolution as it came up really low with a default res of 800x600.

So I go into System>Preferences>Display

The monitor is shown as unknown and I only two resolution setting available.  800x600 (4:3) or 640x480(4:3)

Clicking on detect monitor does nothing.  

So what do I do?  I can barely see anything with my display so screwed up.

Thanks!


My computer is a Dell Inspiron Desktop 545s SlimTower
Processor: Intel Core 2 Duo Processor E7400 (2.8GHz, 3M, L2Cache, 1066FSB)
6 GB DDR2 SDRAM 800MHz (4 DIMMs)
750 GB SATA Hard Drive (7200RPM)
I dont know what the integrated graphics card is and I don't know how to check

My monitor is a Samsung SyncMaster 997MB

---

### Post by Sanjuro82 on 2009-10-15
Anyone know the solution?

---

### Post by Sanjuro82 on 2009-10-15
I ran lspci, and here are the results:


00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by bab1 on 2009-10-15
> **Sanjuro82 said:**
> This is very annoying.  I just installed 9.10 beta on a new Dell computer.  I started from scratch and did a fresh install.  Everything went smoothly.  After the install and reboot, i tried to change my resolution as it came up really low with a default res of 800x600.

So I go into System>Preferences>Display

The monitor is shown as unknown and I only two resolution setting available.  800x600 (4:3) or 640x480(4:3)

Clicking on detect monitor does nothing. 

So what do I do?  I can barely see anything with my display so screwed up.

Thanks!


My computer is a Dell Inspiron Desktop 545s SlimTower
Processor: Intel Core 2 Duo Processor E7400 (2.8GHz, 3M, L2Cache, 1066FSB)
6 GB DDR2 SDRAM 800MHz (4 DIMMs)
750 GB SATA Hard Drive (7200RPM)
I dont know what the integrated graphics card is and I don't know how to check

My monitor is a Samsung SyncMaster 997MB

The new Xorg.conf file is supposed to automagically take care of the settings.  If it does not recognize your monitor or vid card it will only give safe settings.

You will need to go in and change the mode line in the /etc/X11/xorg.conf file.  Here is the relevant section from my file.  Use at your own risk.```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection
        
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1600x1200" "1440x900" "1400x1050" "1280x1024" "
        EndSubSection
EndSection

```

---

### Post by Sanjuro82 on 2009-10-15
In terminal I ran 'cat /etc/X11/xorg.conf'

and the result is:
cat: /etc/X11/xorg.conf: No such file or directory


Do I not have a xorg.config file?????

---

### Post by bab1 on 2009-10-15
Sanjuro82,

Change into the /etc/X11 directory.  See what is there.

Curious...

---

### Post by Sanjuro82 on 2009-10-15
I browsed to /etc/x11/   in Nautilus.  I don't see any xorg.config file.

---

### Post by bab1 on 2009-10-15
> **Sanjuro82 said:**
> I browsed to /etc/x11/   in Nautilus.  I don't see any xorg.config file.

Being really picky; it's /etc/**[COLOR="Red"]X[/COLOR]**11/xorg.**[COLOR="Red"]conf[/COLOR]**.  But as you say that nothing of that type is there, then so be it.

I would see if you have an alternate version somewhere.  Try finding it with the command *locate*, like this```
locate xorg.conf
```

EDIT: If you can't find one then you might try reconfiguring it like this```
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Sanjuro82 on 2009-10-16
I used 'sudo gedit /etc/X11/xorg.conf'

and my xorg.conf is blank.  Can anyone paste the default xorg.conf text for me so I can update mine?
Thanks

---

### Post by bab1 on 2009-10-16
> **Sanjuro82 said:**
> I used 'sudo gedit /etc/X11/xorg.conf' and my xorg.conf is blank.  

That's because, as you said before, it does not exist.> Can anyone paste the default xorg.conf text for me so I can update mine?
Thanks

When you perform the reconfigure a new xorg.conf file will be generated.  Once again try```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

