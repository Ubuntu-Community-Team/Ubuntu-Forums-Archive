---
title: "GeForce 210 card- system won't boot"
date: 2011-08-03
forum: General Help
---

### Post by sumithar on 2011-08-03
I installed a zotac geforce 210 PCI-E card.  I made the necessary bios setting for display.

After I turn on the machine I see just the initial HP Invent screen.  The boot process is not happening.

Do I need to install some drivers before hand while I am connected to my onboard display?  The only CD I have is for Windows drivers so not sure what I can download.

Googling reveals some talk about Nvidia drivers but nothing specific.

Thanks!

---

### Post by fragos on 2011-08-03
With modern BIOS there is no configuration required to add a video card. It should be automatically detected and used instead of the on board video. Not sure what you could have changed. If your mobo had an ATI chip set your system may be booting with a driver that won't work. The 210 will work with the default VESA driver, just not the 3D rendering. Used to be that xorg.conf set the video driver but that no longer seems to be the case. My 210 works perfectly after being installed on a mobo that had an Nvidia 7025 chip set.

---

### Post by sumithar on 2011-08-06
> **fragos said:**
> With modern BIOS there is no configuration required to add a video card. It should be automatically detected and used instead of the on board video. Not sure what you could have changed. If your mobo had an ATI chip set your system may be booting with a driver that won't work. The 210 will work with the default VESA driver, just not the 3D rendering. Used to be that xorg.conf set the video driver but that no longer seems to be the case. My 210 works perfectly after being installed on a mobo that had an Nvidia 7025 chip set.

Hi thanks for the reply...I don't get it all but I'll attempt to respond.

Mine is not a "modern" bios, I think but it does take DDR2 memory, so not 
ancient either.

Your surmise that I might have onboard ATi is correct, I think, since I see this bit when I execute lshw
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:d0000000-dfffffff ioport:d000(size=256) memory:feaf0000-feafffff memory:feac0000-feadffff


Can I do anything to get around this?

This is some other information from motherboard pertaining to BIOS
    description: Desktop Computer
    version: 0p]1211CT101ALHEN10
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 family=103C_53316J sku=RB042AV#ABA uuid=2C158E48-FE52-DB11-B108-28361328E31A
  *-core
       description: Motherboard
       product: Alhena
       vendor: Hewleet-Packard
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.18
          date: 08/17/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot


Thanks again.

---

### Post by fragos on 2011-08-06
This used to work but there's been so many changes to the startup process that I'm not positive. Make a backup of /etc/X11/xorg.conf and then add the following 4 lines before rebooting.

Section "InputDevice"
Identifier "video"
Driver     "nvidia"
EndSection

---

### Post by sumithar on 2011-08-08
> **fragos said:**
> This used to work but there's been so many changes to the startup process that I'm not positive. Make a backup of /etc/X11/xorg.conf and then add the following 4 lines before rebooting.

Section "InputDevice"
Identifier "video"
Driver     "nvidia"
EndSection

I don't even find a file called xorg.conf in there.  Should I create one with just these 4 lines?
THis is the directory listing
/etc/X11$ ls -la
total 88
drwxr-xr-x  10 root root  4096 2011-07-02 12:22 .
drwxr-xr-x 137 root root 12288 2011-08-08 20:30 ..
drwxr-xr-x   2 root root  4096 2011-04-25 19:05 app-defaults
drwxr-xr-x   2 root root  4096 2011-04-25 19:05 cursors
-rw-r--r--   1 root root    14 2011-04-25 19:04 default-display-manager
drwxr-xr-x   4 root root  4096 2011-04-25 19:00 fonts
-rw-r--r--   1 root root 17394 2010-02-18 19:02 rgb.txt
lrwxrwxrwx   1 root root    13 2011-05-05 22:20 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2011-04-25 19:05 xinit
drwxr-xr-x   2 root root  4096 2011-02-08 08:27 xkb
-rwxr-xr-x   1 root root   709 2010-11-02 17:17 Xreset
drwxr-xr-x   2 root root  4096 2011-07-02 12:22 Xreset.d
drwxr-xr-x   2 root root  4096 2011-07-02 12:22 Xresources
-rwxr-xr-x   1 root root  3730 2010-12-01 22:34 Xsession
drwxr-xr-x   2 root root  4096 2011-07-28 08:11 Xsession.d
-rw-r--r--   1 root root   265 2010-02-18 19:02 Xsession.options
-rw-r--r--   1 root root   601 2011-04-25 18:54 Xwrapper.config

---

### Post by fragos on 2011-08-08
Create the file. It's not supposed to be needed but will be used if there. Also I made a mistake, it should be Section "Device".

---

### Post by sumithar on 2011-08-10
> **fragos said:**
> Create the file. It's not supposed to be needed but will be used if there. Also I made a mistake, it should be Section "Device".
Hi,
I did as you suggested.
Then I reinserted the pCI-E card and attached the monitor to that.
Restarted the computer.
Same result- it just sits on the HP splash screen.

Switched off, unplugged, removed the PCIE card and reattached monitor to the onboard VGA.
Rebooted, now it won't boot, most prolly 'cos the xorg.conf is throwing it off.

Booted from CD, removed the xorg.conf and then removed the boot CD

Now I'm back to where I was before I started to play with the PCI-E card.

I'm somehow inclined to think this has aught to do with Ubuntu, it's some kind of hardware issue.

If you're by now out of suggestions, that's fine- thanks for trying!
Rgds

---

### Post by fragos on 2011-08-10
There's a chance no nvidia drivers were actually installed so I suggest you try xorg.conf again only this time with:

Driver "vesa"

vesa works with everything and should be there. If it starts up OK use the "Additional Drivers" preferences to select nvidia. If that doesn't work I am truly out of suggestions.

---

### Post by sumithar on 2011-08-13
Hi,
No, that didn't take either.  I don't even know if it is getting as far as the boot process since it freezes on the splash screen.  I will try with someone else who has a PCI-E slot and if it still doesn't work, give it up.

Thank you so much for all your help.

---

### Post by Wim Sturkenboom on 2011-08-13
Press <shift> while booting; you should get the grub menu. The line that will be used during the standard boot is highlighted. Press 'e' to edit. Find the line that ends with *_quiet splash_*; this is a long line and probably wrapped. Go to that line (using the cursor keys) and remove the words and add *_nomodeset_*. Next press <ctrl>x to boot.

What is does:
Removing those two words makes that you're no longer blind and can see what's going on.
Adding nomodeset instructs the kernel to not set the mode (whatever that might be ;) ); it probably 'disables' the nouveau video driver.

Not said that it's the solution, but not tried is always missed :)

If it works, you can make it permanent.

---

### Post by sumithar on 2011-08-14
Hi Wim,
Thanks for your input.
Unfortunately, it stays stuck on the HP Logo splash screen and doesn't respond to any keystroke.  I tried pressing the shift key as soon as I power on the machine  but it doesn't budge past the HP Logo splash screen.

---

### Post by cryptotheslow on 2011-08-15
So at the point it's "stuck" at the splash screen even pressing Caps Lock or Num Lock fails to toggle the lights for them? If so it's a hard lock-up.

Does the PCI-E card require its own power connector and have you connected it?

Just a thought, the card maybe pulling too much power from the PCI-E slot itself causing the board to flake out.

Try burning a LiveCD ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)) and booting up from that with the new card in place. At least that would help eliminate any previous ATI related configs that may exist on your install.

I'm surprised there is no option to disable the onboard VGA controller completely in the BIOS :o

---

### Post by Derek Karpinski on 2011-08-15
I have that card, and an HP computer.
 
Just to confirm, you did change the BIOS to point ot the PCI-E video card?
 
If so, the first thing you should see before the HP splash is an nVidia BIOS screen.  The video card fan should spin up, then the nVidia info, then HP splash.
 
If it doesn't.......I don't know.......mine was P'nP.:confused:

---

### Post by sumithar on 2011-09-13
> **Derek Karpinski said:**
> I have that card, and an HP computer.
 
Just to confirm, you did change the BIOS to point ot the PCI-E video card?
 
If so, the first thing you should see before the HP splash is an nVidia BIOS screen.  The video card fan should spin up, then the nVidia info, then HP splash.
 
If it doesn't.......I don't know.......mine was P'nP.:confused:

Derek- yes, I did change the BiOS to point to PCI-E.
I didn't see that nVidia screen at all.

I'm going to give up for now- thanks all who replied

---

