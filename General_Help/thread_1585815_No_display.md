---
title: "No display"
date: 2010-10-01
forum: General Help
---

### Post by grumpy.biatch on 2010-10-01
Hi,

I dont see display in UbuntuStudio amd64. 

Here are errors -

```
startx
xauth:  creating new authority file /root/.Xauthority
xauth:  creating new authority file /root/.Xauthority


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntustudio 2.6.32-25-preempt #44-Ubuntu SMP PREEMPT Fri Sep 17 22:21:55 UTC 2010 x86_64
Kernel command line: root=/dev/sda16 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct  1 14:25:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.

xinit:  No such file or directory (errno 2):  unable to connect to X server

xinit:  No such process (errno 3):  Server error.
root@ubuntustudio:/home/david# gdm
gdm-binary[1683]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
gdm-binary[1683]: WARNING: GdmDisplay: display lasted 0.173321 seconds
gdm-binary[1683]: WARNING: GdmDisplay: display lasted 0.153026 seconds
gdm-binary[1683]: WARNING: GdmDisplay: display lasted 0.166784 seconds
gdm-binary[1683]: WARNING: GdmDisplay: display lasted 0.158640 seconds
gdm-binary[1683]: WARNING: GdmDisplay: display lasted 0.161281 seconds
gdm-binary[1683]: WARNING: GdmDisplay: display lasted 0.162768 seconds
gdm-binary[1683]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
root@ubuntustudio:/home/david# nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

root@ubuntustudio:/home/david# startx


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ubuntustudio 2.6.32-25-preempt #44-Ubuntu SMP PREEMPT Fri Sep 17 22:21:55 UTC 2010 x86_64
Kernel command line: root=/dev/sda16 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) n
```

How do I get display working.

---

### Post by dino99 on 2010-10-01
so what is your graphic card/chipset ? you need to install its driver.

sudo rm -f /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo apt-get install xserver-xorg-video-nouveau

then reboot and check driver activation (system admin additional driver)

---

### Post by grumpy.biatch on 2010-10-01
> **dino99 said:**
> so what is your graphic card/chipset ? you need to install its driver.

sudo rm -f /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo apt-get install xserver-xorg-video-nouveau

then reboot and check driver activation (system admin additional driver)


Here are chipset details -

```
lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```

i was booting studio till yesterday. installed suse grub in morning and there after unable to get the x working. i've 2 more flavors of Ubuntu on my machine and they work fine without any trouble.

---

### Post by dino99 on 2010-10-01
so i guess that this " suse grub" is widely different of the maverick's one. AS you have a multiboot system, better to use the "maverick grub-pc" to boot them all

is the "suse grub" grub1 or grub2 ?

As your video card is nvidia, when you check driver activation, you might see nvidia-current activated into: system admin additional driver.

---

### Post by grumpy.biatch on 2010-10-01
> **dino99 said:**
> so i guess that this " suse grub" is widely different of the maverick's one. AS you have a multiboot system, better to use the "maverick grub-pc" to boot them all

is the "suse grub" grub1 or grub2 ?

As your video card is nvidia, when you check driver activation, you might see nvidia-current activated into: system admin additional driver.

I installed propriety driver immediately post system update in UbuntuStudio. SUSE grub is Legacy GRUB and with that I can load BSD, Solaris, etc. I tried GRUB 2 off caeLinux but that returned few errors over BSD, Solaris, PCLinuxOS & Mandriva. SUSE GrUB looks nice and one can configure it easily. 

Here is xorg.conf from UbuntuStudio

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1716W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by grumpy.biatch on 2010-10-01
Got the display back. 

Thanks, dino99!

---

