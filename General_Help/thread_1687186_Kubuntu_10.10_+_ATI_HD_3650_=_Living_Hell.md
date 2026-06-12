---
title: "Kubuntu 10.10 + ATI HD 3650 = Living Hell"
date: 2011-02-13
forum: General Help
---

### Post by jupdown on 2011-02-13
I think I will start this off by giving you my system specs:

Core 2 Duo 2.4ghz
2gb DDR2
ATI HD3650 1gb [(this guy)]("http://www.diamondmm.com/3650PE1G.php")

I recently made a purchase of a new laptop that outdoes this system in every way possible for gaming. I decided that I would be a smart man to install linux on it and use it as a media centre pc since it has a 2TB hard drive on it with 2 1080p monitors. So I install Kubuntu on it and out of the box it runs fairly well. the windows and menu run a little buggy so I decide to install ATI's proprietary driver. then **** hits the fan and my system goes slow as hell. I uninstall the drivers and get the latest version from their website. It runs slightly better but still like a 3 legged dog on stilts.

If anyone has some protips on making my pc run faster please let me know... If this keeps up then I think I'm gonna have to go back to windows because this is way to slow.:(

---

### Post by Eruaran on 2011-02-21
I know how you feel. Tonight I'm going to try the latest Kubuntu 11.04 alpha and came here to see if things have improved with ATI/AMD graphics.

I have a 9400GT and HD3650, and the latter is definately the better card but I have never been able to see and enjoy my system running the way I want it with the HD3650.

I really want to use it, but I can't get what I want out of it and I don't want to spend a week pulling my hair out looking for a solution when there just isn't one.

The best I have been able to get even after much screwing about is nice smooth desktop effects, but guaranteed system lock up if I want to play games OR beautifully smooth gameplay but it guaranteed I cannot have desktop effects at all. Frankly I'm sick of it. I want my system to work the way I like it and I'm putting this squarely at ATI/AMD's feet. They have had forever to provide decent driver support. Intel can do it, and Nvidia can do it (even though I don't like proprietary drivers - at least everything works nicely). But ATI/AMD completely fails.

Great graphics card. Miserable driver "support".

The day I bother with AMD graphics again on Linux will be the day I hear Linux users singing AMD's praise for wonderful and open driver support.

Talk is cheap AMD. :evil:

---

### Post by mastablasta on 2011-02-21
noooooo please say it isn't so. i planned to put Ubuntu on my computer in a year or so...
 
anyway on a side note i have the 512 Mb version if this card. and i tried Ubuntu 10.04 (live session) on it and it worked fine and fast. i am not sure why you have a slowdown. just for fun i think i will try Kubuntu 10.10 via USBlive when i get home. i wonder if it works nicelly.
 
hmm perhaps Xconf is not propperly configured? then again i never went as far as to actually try the proprietary drivers.
 
also the other computer has no issues with ATI opensource drivers (Radeon 9600XT) it does have issues with Intel HD sound chip.

---

### Post by mastablasta on 2011-02-21
update / i am writing this in rekonq on 10.10 live. i see no issues here. ok mazbe a bit slower but it-s a live USB.

here is the lspci:
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
02:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

i also enabled plenty of effects and i see no issues.

though as i said mz card is 512 MB. maybe an odler chip is inside?

---

### Post by Eruaran on 2011-02-21
Well, I decided to give it just one more shot with Kubuntu 11.04 Natty Alpha 2. It's installed and things are mainly running fine (it is an alpha after all). Graphics are ok but a bit laggy. I haven't been brave enough to install the proprietary drivers yet. Will let you know what happens.

If I have any trouble I'm just going to start from scratch with my nvidia card.

---

### Post by mastablasta on 2011-02-22
oh one thing my audio was recognised but there was no sound. the only issue i noticed... anyway i will now try the same with Ubuntu 10.10 and after that debian 6, just to see how it goes.
 
edit-update: also Ubuntu 10.10 works nicely and speedy (even with opensource drivers). Also sound on my mobo apparently works. i had it muted. silly me. :-)

---

### Post by Eruaran on 2011-02-23
Well I tried installing the driver from ATI/AMD and followed instructions exactly. Upon reboot I saw a segfault and could no longer start x at all. I decided on the spot that I'm not prepared to waste time trying to sort that out. I shut my system down, replaced the card with my Nvidia card and reinstalled.

Sorry... not gonna waste more time on ATI/AMD.

---

### Post by mastablasta on 2011-02-23
> **Eruaran said:**
> Well I tried installing the driver from ATI/AMD and followed instructions exactly. 
 
mmmkey... if this is for 11.04 natty i doubt the drivers out here are ready for it already. last time they worked with cannonical to release it in time for 10.10.
 
what instructions? you are supposed to install them from Hardware drivers menu. no?
 
 
yah use what works for you. if you have a spare card why not. currently i wish i had a compatible sound card lying arround :-)

---

