---
title: "Cannot Get 10.04 working with Nvidia 8400 GS"
date: 2010-06-12
forum: General Help
---

### Post by Agerak on 2010-06-12
This is my first post and I am relatively new to Ubuntu, please be gentle ):P

I am running Ubuntu 10.04.
Hardware is as follows:
D945GCLF2
2GB Ram 667Mhz
120GB WD Drive
External USB DVD-Rom

I can install and run the OS perfectly with this setup.

Once I add an Nvidia 8400GS Video Card via PCI, the system will no longer boot into the OS.  I also get errors when trying to boot into the Live CD as well.  I will copy the error message details over at a future date because currently this is my only working system.  They did have something to do with low level memory corruption or some such with a warning about potential  BIOS corruption.

Once the 8400GS is removed, the system will boot normally if a bit slower than normal (on first boot after removal).

If anyone has any ideas or any advice, I would welcome it :confused:

---

### Post by bwallum on 2010-06-12
Hi

I run nVidia cards and they have all worked so provided your card is sound I'm sure we can get something going.

Firstly, do you have a motherboard with on-board LAN? Your motherboard spec says so

> The Intel Desktop Board D945GCLF2 is designed to support Internet-centric computing, delivering incredible capabilities in the flexible Mini-ITX form factor. Featuring the integrated 45nm dual-core Intel Atom processor 330 and the Intel 945GC Express Chipset

If so then get into your BIOS menu, usually called Setup and usually at boot you will be told which key to press. Common ones are Del, F1, F2, F10, and Esc.

Once you get to your BIOS menu make sure that you make the primary graphics driver your NVidia card. It may offer PCIx or something similar. Select it, save and turn off your machine. Insert the graphics card and reboot.

Let us know what happens.

---

### Post by Agerak on 2010-06-12
I swapped out the video card and that seems to have solved my issue.

I did not think that the card was bad as it was in a working XP system beforehand.

Thank you for your advice, I still had to change the settings for it to work properly.  I appreciate the very prompt reply :p

---

### Post by bwallum on 2010-06-12
Welcome to the Ubuntu Forums, I've always found them prompt myself. I guess you could sum it up as 'don't suffer, just ask'.

All the best
Bob

---

### Post by Agerak on 2010-06-16
GAH! I must reopen the thread.

For some reason, my card which was exchanged began exhibiting the exact same behavior as the previous card after a reboot.

I swapped it again (3rd Card) and same exact issue.

I plan on removing the board and card from the chassis and testing without the 90 degree PCI adapter used in the slim chassis.

If anyone has any additional ideas as to what would cause this issue, I welcome the help.

---

### Post by bwallum on 2010-06-16
Agerak, try starting a new thread. Say which hardware you are trying to plug the nVidia GS card into. Also say if the card is PCI express or AGP? (Has it got two notches in the pin strip -pcix or one -agp; and just to confuse some two notch work in both) Say which OS you are using 32 or 64bit and say if your bios supports a motherboard graphics chip and also if you have set your bios to use pcix or agp as primary (that is don't use the onboard graphics chip)

I'll follow, just want more minds better than mine on the job. Post the thread number here so that I'll know where to go.

Rgds
Bob

---

### Post by ukripper on 2010-06-17
> **Agerak said:**
> GAH! I must reopen the thread.

For some reason, my card which was exchanged began exhibiting the exact same behavior as the previous card after a reboot.

I swapped it again (3rd Card) and same exact issue.

I plan on removing the board and card from the chassis and testing without the 90 degree PCI adapter used in the slim chassis.

If anyone has any additional ideas as to what would cause this issue, I welcome the help.

Boot into  recovery mode from grub screen. Then select the option of root.
Once on root prompt type below command:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

and then ```
reboot now
```

It should work fine now and if it doesn't post back again with any error message.

---

### Post by Agerak on 2010-06-17
[COLOR=White]How do I go about booting into the recovery mode?  A  quick Google search wasn't very helpful.[/COLOR]
Please [COLOR=Black]ignore the above, I managed to find it, space will  enter said mode.[/COLOR]

A minor update:

My system is currently fully functional while the onboard video is used,  despite the card being installed.  Only when I change BIOS to the  external PCI Graphics do I have issues on booting.  I am currently  installing the Nvidia Drivers and after a reboot to insure system is  still functional with onboard video, I plan on changing BIOS and seeing  what happens.

Assuming that fails I will attempt the previous posts suggestion.  Wish me luck :)

---

### Post by Agerak on 2010-06-17
I tried activating the Nvidia driver inside Ubuntu, but when I reboot, I get no video after the small ubuntu splash screen during load (still using on-board Graphics).  After changing to external graphics, I still get the error messages "Corrupted low level memory..." line after line after line.

I tried pressing SPACE to get into the GRUB recovery mode, but nothing happened.  I had video, but only a black screen with nothing on it (Video was active, just nothing that I could see).

I have tried numerous reinstalls of the system, both with and without the card installed and both with and without the card active.  Uninstalled inactive works perfectly.  Installed inactive works perfectly, as soon as the card is activated I get "Corrupted low level memory..." errors aplenty.

I have run numerous full memtest runs overnight with the card in and active and they all come back fine.

I am trying really hard to convert over to ubuntu, at least on this shared machine so that it isn't completely screwed up by my siblings, but I've never had these kinds of problems with Windows (granted I had a host of other problems instead).

Any further help is appreciated and bear in mind that I know absolutely nothing about the under-workings of linux so any steps I should take, please make them as easy to follow as possible.

Thank you for your help.

---

### Post by bwallum on 2010-06-17
> Only when I change BIOS to the  external PCI Graphics do I have issues on booting. 

When you are in the CMOS setup menus, what is offered regarding choice of graphics?

---

### Post by Agerak on 2010-06-17
My options are
Auto (rarely used)
Internal Graphics (IGD)
and External Graphics (PCI)

---

### Post by Agerak on 2010-06-17
I may have found something.

(Still running with on-board video as primary with expansion 8400 card installed but disabled)

When I run a program called sysinfo the drop-down info on left side has Nvidia, I select and go to NVIDIA Display Settings and it gives me the following error message:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

How would I go about doing this?  When I run the command     nvidia-xconfig     from a terminal I get the message:

WARNING: Unable to locate/open X configuration file.
ERROR: Unable to write to directory '/etc/X11'.

Does this help at all?

---

### Post by yossell on 2010-06-17
Just an observation:

Running nvidia-xconfig in a terminal is not running it as root. I think that's the reason for the error message

Entering:  
sudo nvidia-xconfig

followed by your password should run it as root. But the warning message looks like there's not even the relevant file there, so not sure this solves everything for you. And be very careful of making changes as root. Let us know how you progress.

---

### Post by bwallum on 2010-06-17
Is this your motherboard please?
> Processor
Intel Atom

Memory
- DDR2 SDRAM
- Support for PC2-4300, PC2-5300
- Up to 2 GB Maximum

Chipset
- Intel 945GC Express / Intel ICH7

Audio
- Sound card Audio output
- Realtek ALC662 Audio Codec
- 5.1 channel surround Sound Output Mode
- High Definition Audio Compliant Standards

Video
- Graphics Controller Intel GMA 950
- Video Memory Dynamic Video Memory Technology 3.0
- Video Memory Installed 224 MB (max)

Expansion Slots
- 1 memory ( 1.8 V ) - DIMM 240-pin ¦ 1 PCI

Storage Interfaces
- Serial ATA-300 - connector(s):
- 2 x 7pin Serial ATA - 2 Device(s) ¦ ATA-100 - connector(s): 1 x 40pin IDC - 2 Device(s)

Interfaces
- 4 x Hi-Speed USB - 4 PIN USB Type A
- 1 x keyboard - generic - 6 pin mini-DIN (PS/2 style)
- 1 x mouse - generic - 6 pin mini-DIN (PS/2 style)
- 1 x parallel - IEEE 1284 (EPP/ECP) - 25 pin D-Sub (DB-25)
- 1 x serial - RS-232 - 9 pin D-Sub (DB-9) ¦ 1 x display / video - VGA - 15 pin HD D-Sub (HD-15)
- 1 x network - Ethernet 10Base-T/100Base-TX/1000Base-T - RJ-45
- 1 x display / video - S-video output
- 1 x audio - line-In - mini-phone 3.5mm
- 1 x microphone - input - mini-phone 3.5mm
- 1 x audio - line-out - mini-phone stereo 3.5 mm

Cables Included

- 1 x IDE cable
- 2 x Serial ATA cable
Software Included

- Intel Express Installer
- 3 years warranty


If you don't know open a terminal (Applications>Accessories>Terminal) and enter this command:```
sudo lshw -c bus
```Copy and paste the returned message here.

---

### Post by Agerak on 2010-06-17
bwallum:
Yes that is my motherboard and below is the output from that command

altex@altex-breakroom:~$ sudo lshw -c bus
PCI (sysfs)  
  *-core                  
       description: Motherboard
       product: D945GCLF2
       vendor: Intel Corporation
       physical id: 0
       version: AAE46416-103
       serial: AZLS904004GU
       slot: Base Board Chassis Location
  *-usb:0
       description: USB Controller
       product: N10/ICH7 Family USB UHCI Controller #1
       vendor: Intel Corporation
       physical id: 1d
       bus info: pci@0000:00:1d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=uhci_hcd latency=0
       resources: irq:23 ioport:3080(size=32)
  *-usb:1
       description: USB Controller
       product: N10/ICH 7 Family USB UHCI Controller #2
       vendor: Intel Corporation
       physical id: 1d.1
       bus info: pci@0000:00:1d.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=uhci_hcd latency=0
       resources: irq:19 ioport:3060(size=32)
  *-usb:2
       description: USB Controller
       product: N10/ICH 7 Family USB UHCI Controller #3
       vendor: Intel Corporation
       physical id: 1d.2
       bus info: pci@0000:00:1d.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=uhci_hcd latency=0
       resources: irq:18 ioport:3040(size=32)
  *-usb:3
       description: USB Controller
       product: N10/ICH 7 Family USB UHCI Controller #4
       vendor: Intel Corporation
       physical id: 1d.3
       bus info: pci@0000:00:1d.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=uhci_hcd latency=0
       resources: irq:16 ioport:3020(size=32)
  *-usb:4
       description: USB Controller
       product: N10/ICH 7 Family USB2 EHCI Controller
       vendor: Intel Corporation
       physical id: 1d.7
       bus info: pci@0000:00:1d.7
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm debug bus_master cap_list
       configuration: driver=ehci_hcd latency=0
       resources: irq:23 memory:a32c4000-a32c43ff
  *-serial UNCLAIMED
       description: SMBus
       product: N10/ICH 7 Family SMBus Controller
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 01
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
       resources: ioport:3000(size=32)

Yossell:
I tried your command and this is the message that it gave me.  I tried to run it twice since I saw that it had made a file on the first run, I thought it might have accessed it on the second.

altex@altex-breakroom:~$ sudo nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

altex@altex-breakroom:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

P.S.
Now I finally understand this comic!
[http://xkcd.com/149/](http://xkcd.com/149/)
:lolflag:

---

### Post by fooman on 2010-06-17
you need to log-out and back in again after running "sudo nvidia-xconfig" for the change to take effect.

---

### Post by yossell on 2010-06-17
The instructions in earlier your post also tell you to restart the x-server after running that command. Did you give that a go?

edit: ah - beaten to it

---

### Post by bwallum on 2010-06-17
> **Agerak said:**
> 
New X configuration file written to '/etc/X11/xorg.conf'

P.S.
Now I finally understand this comic!
[http://xkcd.com/149/](http://xkcd.com/149/)
:lolflag:

Excellent humour! Did the re-config do it for you? If not could you post the output of ```
sudo lshw -c display
```please.

---

### Post by Agerak on 2010-06-17
I tried the reset nvidia, but after rebooting and changing BIOS to external, it still gave me the errors.  I switched back to on-board, but got no video (black screen, video feed is active, didn't get 'no signal' message on monitor).  I had to completely remove the card and then it booted with an error stating that the system must run in low graphics mode and I had to reset the display settings in order to get back into ubuntu.

Here is the read out from your command.

altex@altex-breakroom:~$ sudo lshw -c display
[sudo] password for altex: 
  *-display               
       description: Display controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:a3200000-a327ffff ioport:30e0(size=8) memory:80000000-8fffffff(prefetchable) memory:a3280000-a32bffff
  *-display
       description: VGA compatible controller
       product: G98 [GeForce 8400 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:a2000000-a2ffffff memory:90000000-9fffffff(prefetchable) memory:a0000000-a1ffffff ioport:1000(size=128)

---

### Post by fooman on 2010-06-17
> I tried the reset nvidia, but after rebooting and changing BIOS to  external, it still gave me the errors.ok, allow me to ask the dumb question:

after you set the bios to external (PCI), you *are* shutting down and physically *removing the cable from the onboard video card and connecting to the nvidia card* before booting up again...correct?

sorry,  i had to ask.

EDIT: btw,  i just picked up a supposedly "broken" dell e319 earlier this week for $10 on craigslist.  has a dvd burner and a new wireless card was installed recently.  i was told it would not start.  brought it home,  found a power cord,  plugged it in and it booted right up to xp.  i picked up an inexpensive PCI 8400gs (no pci-e or agp on this mobo),  through in 2 gigs of ram that i had onhand,  popped in my lucid cd,  wiped out xp and installed ubuntu.  everything worked on first boot.

runs great!

---

### Post by bwallum on 2010-06-17
From the specification it appears that you have a pci expansion slot. Not a pcix expansion slot. If that is the case then your pci express graphics card will not work properly. You will be able to see it but the card will need the bandwidth of a pcix slot (16 times that of a pci slot) to work correctly.

Did your graphics card work in your hardware for Windows?

---

### Post by Agerak on 2010-06-17
lol Fooman.  Yes I did change the cable, but sometimes the most obvious and stupid question is sometimes the most important :)

Although I am very new to Ubuntu, I have been using Windows PCs for some time.  Basic config (BIOS, Hardware, where things plug in) I am very familiar with, it is the working and configuring of Linux/Ubuntu which I have 0% comprehension on.

The card I am using is a PCI card.  It works perfectly fine in XP (it was pulled from another system) and also worked great in Win7 with the exact same setup as I am currently using.

When my brother borked that system with a virus, I decided to give Ubuntu a shot as it was highly recommended by fellow co-workers.  Unfortunately, their systems were lucky in that they just worked.  Mine on the other hand hasn't and they have no more a clue about what to do than I do.

My understanding of the 8400GS PCI is that it is based on the exact same 8400GS GPU which was designed for PCIEx16 and they retrofitted it with an adapter chip and a standard PCI interface to create a simple, decently powerful PCI based card.

---

### Post by fooman on 2010-06-17
the 8400gs (pci) is a decent card.  as i said in the edit of my last post: i just installed one earlier this week and am quite pleased with the results.  handles compiz fine, and i had the dual display working with the vga going out to a 17" lcd monitor and the dvi going out to my 50" plasma (dvi to hdmi cable)....handled that well also. 720p/1080p play really nice with the nvidia drivers installed & vdpau enabled.

just to rule everything out...have you tried a different pci slot?  and if card has different outputs (vga/dvi/hdmi)....have you tried all of those as well?

---

### Post by Agerak on 2010-06-17
the mobo that I am using is an ITX and as such, only has a single PCI slot avaliable :(

As for the different slots, I have, during testing, hooked up monitors to all 3 ports (Onboard VGA, 8400GS VGA, 8400GS DVI)  All of the test monitors were 19" or smaller, well within resolution limitations of all ports involved.

With the card enabled, it seemed to want to use DVI first (still got lots of errors though as stated above)  The onboard works perfectly, even with the card installed, it is only when I enable the card as the primary display that I have the errors.

---

### Post by bwallum on 2010-06-18
Found this at [http://www.dabs.com/products/pny-geforce-8400gs-576mhz-512mb-pci-vga-dvi-i-5K9L.html#reviews](http://www.dabs.com/products/pny-geforce-8400gs-576mhz-512mb-pci-vga-dvi-i-5K9L.html#reviews)

> Good choice for Atom systems with PCI slots
Reviewed by Anonymous Review Posted 06/11/2009

Bought this to use with a D945GCLF2 Intel Mobo.

After a bit of poking it now will play 1080p footage perfectly with XBMC Live.

Make sure to blacklist the Intel GPU like so:

Add the following lines to your /etc/modprobe.d/blacklist file:

blacklist intel_agp
blacklist agpgart

Then ensure you enable VDPAU in the Player -> Render Options (change from Autodetect)

Voila! 1080p playback - with less than 10% CPU load.

Not bad for PCI :)
Looks as though you have to blacklist the on board graphics to get streaming to work. Might it help with pci graphics cards generally??

To edit the blacklist file use a terminal with this command:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

I've set up a thread with nvidia forum [http://forums.nvidia.com/index.php?showtopic=171805](http://forums.nvidia.com/index.php?showtopic=171805) to see if we can get more light on the subject.

Also posted a new thread on the Ubuntu hardware forum [http://ubuntuforums.org/showthread.php?p=9477561]("http://ubuntuforums.org/showthread.php?p=9477561")

---

### Post by Agerak on 2010-06-18
I'm not really trying to get streaming to work.  All I want is to use the PCI graphics as primary without the system spazzing out and failing to boot up.

Is there a chance it could be because the shared video memory of the PCI card (which is larger than the onboard I believe) is trying to take an area of memory that Ubuntu requires?  That could be the reason for the memory error codes.

Thankyou for the additional threads.  I have subbed them both.

On a somewhat unrelated note, do you think it would be wise to try a different distribution of linux or ubuntu?  The main reason I went to ubuntu was a friends suggestion as this is a shared family computer and my siblings are notorious for infecting any Windows PC necessitating a reinstall of the OS.  If there is another distro which might have less issues with my configuration, I would be more than happy to give it a try.  This system is only used for Internet and basic office tasks such as writing school essays.

---

### Post by bwallum on 2010-06-18
> **Agerak said:**
> I'm not really trying to get streaming to work.  All I want is to use the PCI graphics as primary without the system spazzing out and failing to boot up.


Agreed, my inference was that you may need to blacklist the onboard graphics chip to get your pci card working. I don't know, I don't have your kit, but I would have thought it a candidate for further exploration. I would just try adding the blacklist entries to the file on your system. You can always remove them. 

USEFUL TO HAVE TO HAND. 
When tweaking the system make sure you have a live cd to hand just in case. If you need to tweak a file from the live cd use ```
sudo nautilus
```and navigate to the appropriate file on the system hard drive.

Ubuntu is a very popular flavour of linux and a lot of resources are involved in developing it. It improves just about daily in my opinion, with a good forum to help get over any hurdles. I would stick with it just for that reason.

---

### Post by Agerak on 2010-06-18
I definitely agree, the forum so far has been absolutely top notch.

I do have one quick question.  I am hesitant to 'test' blacklisting the onboard video because if it fails, I don't know how to 'undo' this change.  I know I can boot into Live CD, but I only know how to reinstall.

I am assuming from live CD, use the Terminal command:

sudo nautilus
gksudo gedit /etc/modprobe.d/blacklist.conf
Am I right in assuming that this would allow me to 'fix' the blacklist, remove the onboard, and reboot back into the HDD using onboard.  I am just hesitant to trying anything that I cannot undo.  I have to try fitting troubleshooting into the normal rotation of sibling use of the system, so anything that takes it down for an extended time (reloading Ubuntu) is problematic, as is reconfiguring for internet favorites, etc.

---

### Post by bwallum on 2010-06-19
If you use the live cd you will be in the live cd environment. To get to the blacklist.conf file in your normal system then use sudo nautilus, find your hard drive where the blacklist.conf file lives, then open it. sudo nautilus will allow you to edit the file and return it to it's previous state. You can just put a # in front of the line to make it a comment (not acted upon).

Or... you could open a terminal and use gksudo gedit /etc/modprobe.d/blacklist.conf.

I'm sure you will but remember to change the monitor lead to the pci card. (Just mentioned it because that's the sort of thing I forget all too easily!)

---

### Post by Agerak on 2010-06-23
I think that I have decided to give up on this issue and simply use the on-board video, however slow it may perform.

As new versions of Ubuntu are released I plan to test them with the Live CDs and see if the issue is fixed.

Thank you for all your great help in attempting to get this problem fixed.

---

### Post by bwallum on 2010-06-23
It can be quite intimidating at first when you come to the forum. There are a lot of guys with a lot of knowledge, mostly they assume stuff that the beginner doesn't really understand. It's ok to tell us to slow down, it's ok to take your time, we just try to help out, as we have been helped out in the past. (Christ, that's almost a prayer...if you'll forgive the pun!)

Don't be put off, we really would like to see you get your card going in accelerated mode...but all in your own time.

Good luck.

---

### Post by sfife on 2010-06-28
I recently updated my 10.04 Ubuntu. Have been running Ubuntu on this machine since 8.10 and after the update just recently my graphics are screwed.
I am using the 8400GS and the max resolution I can get on the recommended restricted driver is 640x480. When I switch back to the 173 Nvidia driver my video colours are bung in TOTEM and VLC can't display a video but plays sound ok but I can get full 1680x1050 using 173.

**Sysinfo**
GeForce 8400 GS
PCI-E 16x
NVIDIA UNIX x86_64 Kernel Module  173.14.22  Wed Nov 11 05:08:25 PST 2009 - Curernt Driver

I have tried a couple of the solutions suggested in this forum to no avail eg sudo nvidia-xconfig.
I have tried adding the correct resolution to my Xorg.config eg.

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
	[B]Viewport	0 0
	Modes	"1680x1050"[/B] *I added these 2 lines*
        Depth       24
    EndSubSection
EndSection

Please tell me if you spot anything in this config that's not right or even if I'm going about it wrong please tell me.

---

### Post by bwallum on 2010-06-28
Go to System>Administration>NVIDIA X Server Settings
Choose X Server Display Configuration
Adjust the resolution to suit...then Save to X Configuration File and do NOT 'merge'. Ignore any error messages when saving.

---

### Post by sfife on 2010-06-28
> **bwallum said:**
> Go to System>Administration>NVIDIA X Server Settings
Choose X Server Display Configuration
Adjust the resolution to suit...then Save to X Configuration File and do NOT 'merge'. Ignore any error messages when saving.

I have tried that. Nvidia's option for resolution max out at 640x480 even after I have included those lines to xorg.conf when attempting to use the recommended driver.
173 works though and I'll have to stick with it as I'm in too deep with Ubuntu atm.

---

### Post by bwallum on 2010-06-28
Try removing the nVidia driver, reboot, then reload the driver. No reason why it should not work. Do you have onboard graphics as well as the pcix card?

---

### Post by ronnielsen1 on 2010-06-28
> Try removing the nVidia driver, reboot, then reload the driver. No  reason why it should not work. Do you have onboard graphics as well as  the pcix card?
I do, I have an Intel on board and the Nvidia 8400GS and I have to download the driver from Nvidia. The Ubuntu method won't work for me. The driver from Nvidia site does install easy though

[http://www.nvidia.com/object/linux-display-ia32-256.35-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.35-driver.html)

---

### Post by bwallum on 2010-06-28
OK...and just to remove the obvious I presume you have set your pcix card as primary in the cmos and followed the install instructions with particular regard to the nVidia kernel setup?
[URL="http://us.download.nvidia.com/XFree86/Linux-x86/256.35/README/installdriver.html"]
http://us.download.nvidia.com/XFree86/Linux-x86/256.35/README/installdriver.html[/URL]

---

### Post by ronnielsen1 on 2010-06-29
> OK...and just to remove the obvious I presume you have set your pcix  card as primary in the cmos and followed the install instructions with  particular regard to the nVidia kernel setup?
[URL="http://us.download.nvidia.com/XFree86/Linux-x86/256.35/README/installdriver.html"]
[/URL]

If this is from my post, yes I had to:

CTRL-ALT-F1

sudo /etc/init.d/gdm stop

cd to my download folder

chmod +x NVIDIA-Linux-x86-256.35.run

sudo ./NVIDIA-Linux-x86-256.35.run

go through the installer

sudo /etc/init.d/gdm start


My bios is A05 and there is no option to disable onboard graphics. The best it will let you is to set it to auto

---

### Post by scooba on 2011-01-05
hi im trying to install ubuntu 10.04 on my pc
gigabyte m68m-s2p mb
amd athlon 64 x2 cpu
nvidea gforce 8400gs gpu
2048 mb memory


i put disc in boot from it and the screen goes to no signal cant
get it to come on no matter what i do

any thoughts...?

thanks

---

### Post by CJ_Hudson on 2011-01-06
Scooba, it could be the type of monitor you are using. Just a thought, try it with a different monitor if you have one available.

---

