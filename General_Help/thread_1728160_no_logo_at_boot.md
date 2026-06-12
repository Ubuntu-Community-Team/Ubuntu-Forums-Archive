---
title: "no logo at boot"
date: 2011-04-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-04-13
there is a logo at shutdown
it acts like it is off the screen to be honest

Ubuntu 10.04.2 64BIT
GeForce GT 430 (i am using the DVI port)
ASUS M4A79XTD EVO Motherboard
AMD Phenom II x4 965
4GB RAM DDR3 1600 (1 stick)
HP 2009m monitor (16x9)
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280×800-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x800

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
``````
sudo hwinfo --framebuffer
[sudo] password for chad: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.nKoKkFdi9hC
  Hardware Class: framebuffer
  Model: "NVIDIA GF108 Board - 1071v1p1"
  Vendor: "NVIDIA Corporation"
  Device: "GF108 Board - 1071v1p1"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xd7000000-0xd7dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

### Post by mikewhatever on 2011-04-13
This is a known issue with plymouth and the proprietary Nvidia drivers. Try the script from [-->here<--]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html").

---

### Post by pqwoerituytrueiwoq on 2011-04-13
i did what that script does manually
if it is giving the boot screen the resolution is over 3200x1800
resulting in the logo being off screen

---

### Post by pqwoerituytrueiwoq on 2011-04-14
odd thing is no matter how i set it i can't even get a boot menu or a press esc to enter menu
all timeouts seem to be bypassed :confused:
My mobo manual has this in it idk if this applies to grub also (F5)
[QUOTE="M4A79XTD EVO Manual"]To access Windows® OS in Safe Mode, do any of the following:
&#8226;     Press <F5> when ASUS Logo appears
&#8226;     Press <F8> after POST.[/QUOTE]

---

### Post by pqwoerituytrueiwoq on 2011-04-16
bump 
it is almost as if the bios is auto confirming grubs default option which i do not mind since this is not a dual boot

---

### Post by pqwoerituytrueiwoq on 2011-04-17
Solution:
Screw grub 2 use classic grub (legacy grub)
[Reverting to GRUB Legacy]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy")

To fix the boot resolution on Nvidia cards on legacy grub
Open [FONT=Courier New]/boot/grub/menu.lst[/FONT]
Find this
[FONT=Courier New]# defoptions=quiet splash[/FONT]
Replace with this
 [FONT=Courier New]# defoptions=quiet splash nomodeset video=uvesafb:mode_option=1280x800-24[/FONT]
change [FONT=Courier New]1280x800-24[/FONT] to the best option you have listed from this command
[FONT=Courier New]sudo hwinfo --framebuffer[/FONT]

you can remove all the stuff you put in there for grub2 like the [FONT=Courier New]framebuffer=y[/FONT] stuff

don't forget to run [FONT=Courier New]update-grub[/FONT] after doing that

---

