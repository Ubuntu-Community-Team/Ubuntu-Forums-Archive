---
title: "No permissions"
date: 2011-01-05
forum: General Help
---

### Post by Zocco on 2011-01-05
hi all

I have just installed ubuntu alongside windows xp and it seems that I dont have permission to do much of anything (that could be an exaggeration.) I tried to load a music cd into rhythmbox and got the error : Error creating directory permission denied.

I also tried to play the cd and although it went through the motions ie. the progress bar moved as the track played and the little pop up window displayed the track details as each new track started there is no sound from the speakers.

I assumed that it could be a driver problem with the sound  card which is a realtek hd audio on the MSI motherboard. I have the installation disc and it contains linux drivers but again when trying to extract the said drives I do not have permission to do so. Why not!!! I installed the O.S. with my password and logged on as me.

Before I run screaming back to windows could anyone please help.

Dave

---

### Post by mikewhatever on 2011-01-05
Permissions is a feature of Linux that doesn't exist in WindowsXP, which makes many XP users somewhat frustrated. I think, before everything else, it's important to understand that Ubuntu is not a free version of Windows, for better or worth, it's different.

> I have just installed ubuntu alongside windows xp and it seems that I dont have permission to do much of anything (that could be an exaggeration.) I tried to load a music cd into rhythmbox and got the error : Error creating directory permission denied.


What do you mean? ;) Did you try playing the cd, or did you try ripping it (encoding into a digital format)?

> I assumed that it could be a driver problem with the sound card which is a realtek hd audio on the MSI motherboard. I have the installation disc and it contains linux drivers but again when trying to extract the said drives I do not have permission to do so. Why not!!! I installed the O.S. with my password and logged on as me.


Please, don't just assume things. Linux has many installation formats, and not all of them are suited for Ubuntu. Before you go about installing drivers, open the Sound Preferences and make sure the volume is not muted.

---

### Post by Zocco on 2011-01-06
Thanks for your interest Mikewhatever, much appreciated.

I tried to do both, ripping the cd and when that failed I tried to play it with the results described. I also tried importing some mp3 files from a windows folder which seemed to work at first but when I clicked on a title to play it nothing happens except the list of tracks goes blank. The music folder is empty 

I have already checked and now rechecked the sound preferences and can confirm that the sound was not muted. When I check the output tab in preferences i see that Dummy output is selected but there are no other options to choose from. I also get no system sounds.

There is also the issue of the "Error creating directory. Permission denied". How can i correct this?

I realise that linux is completely different to windows and I have a lot of learning to do. I have read several beginners articles on the subject but nothing seems to cover these particular issues.

Thanks

---

### Post by mikewhatever on 2011-01-06
The dummy output device in the Sound Preferences means your sound card isn't properly recognized and configured. Try walking through the first 2 stages of the [Comprehensive Sound Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") and post the outputs you get.

On the permissions problem, first, here is a simple run down on permissions.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
Where exactly did you try creating that folder? Try creating it in your home directory instead.

---

### Post by Zocco on 2011-01-07
Here is the output you requested. As you can see there are no playback hardware devices listed in the first part but there is an audio device listed at the bottom of the second list.
 I have not yet checked out the permissions part but I assumed that the correct folder would have been automatically selected by Rythmbox especially because there was no option to select a folder when ripping the cd. Am I asking too much? As far as I can see there is no option in Rythmbox to select a directory for the music files.

Could the lack of transfer of the mp3 files from a windows folder be due to the fact that the folder resides on an NTFS formatted disc. I have just read in a magazine that only windows can read the NTFS format and that for access by other operating systems one of the FAT formats should be used.?

Thanks for your continued assistance.

Dave.

dave@dave-MS-7253:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****

dave@dave-MS-7253:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
    Subsystem: VIA Technologies, Inc. K8M890CE Host Bridge
    Flags: bus master, medium devsel, latency 8
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64
    Kernel modules: amd64-agp

00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
    Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: dfb00000-dfbfffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dc000000-deffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: 00000000dfd00000-00000000dfdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    I/O ports at f400 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at fa00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at f900 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at f800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at f700 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at f600 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at dffff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
    Subsystem: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
    Flags: medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Subsystem: VIA Technologies, Inc. Device 337e
    Flags: bus master, medium devsel, latency 64
    Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at f200 [size=256]
    Memory at dfffe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
    Flags: bus master, fast devsel, latency 0

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: dfa00000-dfafffff
    Prefetchable memory behind bridge: 00000000df900000-00000000df9fffff
    Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1) (prog-if 00 [VGA controller])
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at de000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nouveau, nvidiafb

04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at be00 [size=256]
    Memory at dfaff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8180
    Kernel modules: rtl8180

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: fast devsel, IRQ 17
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

dave@dave-MS-7253:~$

---

### Post by mikewhatever on 2011-01-07
Hi again,
I haven't had a chance to research the sound problem you have, but a quick search suggests it may be a bug in Ubuntu 10.10, which I assume is the version you have. Is that correct? There are several bug reports on launchpad.net, and a possible workaround.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/664785](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/664785)
> Strangely this is related to bug#536699. Changing, in the BIOS, the graphics aperture size from 128MB to 256MB as suggested in that bug's comments solves both that issue and this.

On to the Rhythmbox problem, you are quite right by saying that it should have defaulted to your home folder. By default Rhythmox will use the Music folder inside you Home folder. Of topic, but the way to change that behavior is under Edit->Preferences->Music Tab, where it says 'Music files are placed in:'. I'd very much like to see that error you get, can you take a screenshot of it (PrntScrn button).

---

### Post by Zocco on 2011-01-08
Hi, Thanks for that.

You correctly assume that I am (trying) to use Ubuntu 10.10. However this was installed through a distribution, if thats the right term, called Pinguy which includes a lot of additional "essential" software and settings. I used this after reading quite a a positive revue and thought it might save me from having do a lot of work later LOL. I hope that this is not part of my problems. Although if necessary I am prepared to ditch this and start again with a clean installation. Although I would be unable to do this for a couple of weeks as I am already over my download limit this month and my ISP is theatening to upgrade me at additional cost. Anyway I digress.

Firstly I followed your suggestion and followed the link to download new audio drivers. I did this via the command line as I could not find the Settings link in the Package manager. Is it me? - what is the matter with me. Things seem to go quite well until finally I get the error messages below. I have included the previous few lines of text to give a flavour of what had gone before but the last two lines are the problem.  

Note, selecting 'linux-headers-alsa-driver-2.6.35-23-generic-pae' for regex '2.6.35-23-generic'
Note, selecting 'linux-headers-alsa-driver-2.6.35-23-generic' for regex '2.6.35-23-generic'
Note, selecting 'linux-alsa-driver-modules-2.6.35-23-generic-pae' for regex '2.6.35-23-generic'
Note, selecting 'linux-alsa-driver-modules-2.6.35-23-generic' for regex '2.6.35-23-generic'
E: Unable to locate package linux-alsa-driver-modules-$
E: Couldn't find any package by regex 'linux-alsa-driver-modules-$'

So no go there then.

With regard to the rythmbox error message, firstly my print screen button refuses to copy anything to the clipboard!!!! consequently I am unable to paste anything into a graphics application to attach here. It looks like I will have to find a third party application for this. However I followed your instructions and found the path to the music library location and it says "Multiple locations set" which is "greyed out" I used the browse button to get to my music folder to set it as my preferred music location but "Multiple locations" refuses to change. I finally had another go at ripping the cd and this time it worked so that seems to be sorted for now,  "One small step..." etc. but I would rather that multiple locations were not set as my music location it does seem a bit meaningless.

---

### Post by mikewhatever on 2011-01-08
_Rhythmbox_
Not sure what the 'multiple locations' entry is, it could be something specific to Pinguy or just a glitch. Anyway, I am glad the permissions problem has now been dealt with.

_Pinguy_
I had to look it up, not bad. :D It seems like the trend is - another day, another Ubuntu derivative. Long live diversity.

_Sound_
I see you've followed Daniel T Chen's (Ubuntu developer) suggestion to install newer alsa modules. You have to add the ':ubuntu-audio-dev' repository first, in other words:

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```

...then install the new modules.

The Settings menu in Synaptic Package manager should be in the menu bar up top, along with File, Edit, Packages and Help. You can also invoke it with alt+s shortcut.

_ISP_
You'll probably make your ISP happy again by disabling automatic updates. Ubuntu releases have quite a lot of those. An alternative way to install updates could be to use a free wifi hotspot or another computer with [Keryx]("http://keryxproject.org/").

_Screenshots_
Ubuntu doesn't use the clipboard (in fact, doesn't have one) for screenshots. There are third party applications, the one included by default is gnome-screenshot (Applications->Accessories->TakeScreenshot). In my case, hitting PrntScrn simply invokes gnome-screenshot.

---

### Post by Zocco on 2011-01-09
I had already added the repository as you describe. The error occurred during the installation phase.

The synaptic Package manager does not appear to have the menu bar that you describe. I cannot get back in for another look or anything else At the moment for that matter(see below).

I now have a more pressing problem of my own making although totally unexpected:oops:](*,). Can grub be repaired from the installation cd or from somewhere outside of linux?

The scenario is that I have the linux o.s. installed on an external 500gig usb hard drive in 3 partitions (swap,system and the largest containing my home folder). The boot order having been changed to look at this drive first. These take up about half of the disc capacity, the remainder is a single partition that was formatted with NTFS. In my infinite wisdom I decided to re format this partition with fat32 to import some music files to see if linux would recognise them but now grub won't load and I can't get into linux. I just get a prompt which says "repair grub" and a cursor. I have had to re order the bios so I can get back into windows, which is where I am now. Is there any hope for me?? I have no wish to reinstall completely at least for the next 10 days due to all the updates that get downloaded with it and the dire situation with my download limit.

---

### Post by mikewhatever on 2011-01-09
Reinstalling Grub from the live cd usually fix the boot issues you describe. [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Ubuntu can read and write to NTFS out of the box, not sure why you wanted to format. FAT32 has some big limitations - no journaling, 4GB file size limit.

I've looked around for screenshots of Pinguy, and found both Synaptic and Nautilus without the menus. That fit must have been achieved through the use of the Elementary theme. Changing the theme will probably get you back to normal.
[http://www.best-website-design-company.com/index.php?linux&release=Pinguy%2010.04.1.2](http://www.best-website-design-company.com/index.php?linux&release=Pinguy%2010.04.1.2)

---

### Post by Zocco on 2011-01-10
Thank you, I repaired grub with your info. I also found the menu bar in the package manager, I think I was looking in the wrong place.:D:D

There is definitely a problem installing the Alsa Driver Module I think the problem lies here.

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev-ppa/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-audio-dev-ppa/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

I get this when using both The Package manager and the terminal. It looks like the web page has moved or something.  So Still no luck with the sound.

---

