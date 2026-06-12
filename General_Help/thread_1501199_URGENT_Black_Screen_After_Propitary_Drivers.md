---
title: "URGENT Black Screen After Propitary Drivers"
date: 2010-06-04
forum: General Help
---

### Post by dewey_daniels on 2010-06-04
I was trying to install the propertiary drives for my nvidia geforce 105m.I blacklisted noveau and installed them from the hardware drivers window. Restarted selected ubuntu from grub and it started like normal. Got the splash screen with the dots but there were green dots all around the words and dots.The dots started changing there color grom orange to white but then that is where the trouble starts. After like 3 or 4 dots the whole screen just goes black with no black light. Any help this is kind of urgent. Is there anyway to get it back to my normal ubuntu or at least get it back my programs and stuff. I try the alt+ctrl+f3 but that doesnt do anything.

---

### Post by dewey_daniels on 2010-06-04
Bump Please Solve

---

### Post by ryan858 on 2010-06-04
At the GRUB menu, select Ubuntu and press E. This is let you edit the boot parameters... At the end of one of the lines (linux /boot/vmlinuz .... ) you should see "ro    quiet splash"... Remove the words quiet and splash, and add "nomodset" (no quotes). Removing *"quiet splash*" will remove the splash screen and enable verbose output of what's going on during boot... If you see any errors, write them down and post it here... If nomodset works and you don't have any problems, then you can re-enable the splash screen.

Once you're done editing the boot options, press CTRL+X to boot with the config.

This will only be used once, and will go back to the default config once you reboot. (default may be the wrong word... It reads the grub configuration file.)

If it works, then you can make the change permanent by editing it into either */boot/grub/menu.lst *or */etc/default/grub*, depending on what version of Grub you have installed. In */etc/default/grub* there is a line called **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**. Add nomodset to it, making sure it's inside the quotes. Then run the command **update-grub**.

---

### Post by dewey_daniels on 2010-06-04
Okay well that atleast got me into Ubuntu. When I started it it went through all th code and no problems.Then it said the was an error and i had to boot into Graphics safe mode. When I try to open the nvidia x server program it says this > You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I do that. > derek@derek-laptop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".


ERROR: Unable to write to directory '/etc/X11'.


Now what do i do.

---

### Post by dewey_daniels on 2010-06-04
PS I also did sudo and it said it wrote it and made a backup but the Nvidia x server said that it didnt and said to do the same thing again.

I was following this guide I think the whole problem is it is detecting my Mobo integrated GPU and not the 105m. > derek@derek-laptop:~$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.fRULN9k9OD4
  Hardware Class: framebuffer
  Model: "Intel(r)Cantiga Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r)Cantiga Graphics Controller"
  SubVendor: "Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 31 MB + 960 kB
  Memory Range: 0xc0000000-0xc1feffff (rw)
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown



PPS Here is the guide. [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by dino99 on 2010-06-04
remove your xorg.conf:

sudo rm -f /etc/X11/xorg.conf if you use karmic or more recent

add this ppa to synaptic repo:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

update, upgrade  and reboot

then check: system admin hardware driver: is it activated ?

---

### Post by dewey_daniels on 2010-06-04
Sorry for all the post but I keep forgetting stuff. The error that makes it want to boot into safe mode is >  (EE) No Device Detected

---

### Post by dewey_daniels on 2010-06-04
1 Have no clue what synaptic repo is
2 Am I supposed to add a file or what
3 what am i am updated upgrading


4 The driver is already activated

---

