---
title: "X fails to load with nvidia driver: &quot;screen(s) found, but none have a usable config&quot;"
date: 2010-05-08
forum: General Help
---

### Post by TeeAhr1 on 2010-05-08
Hey guys. I'm going crazy here, hopefully somebody can give me a hand.

My system is a Lenovo B500 All-In-One, with an Nvidia GTS 250M video card. nv seems to work okay, but I cannot get the desktop to load with the nvidia driver (nvidia-current, from the repository). I've been hacking away at this for a week and a half with no results. Every time I try to boot with the nvidia driver, the splash screen comes up for a second, the screen flashes a couple times between a "static" screen and tty2, then the screen seems to go to a test mode, where it flashes a series of solid colors indefinitely. Looking at /var/log/Xorg.0.log, I see the following:

```
(II) May 08 19:06:53 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 08 19:06:53 NVIDIA(0):     enabled.
(WW) May 08 19:06:54 NVIDIA(0): Failed to enable display hotplug notification
(II) May 08 19:06:54 NVIDIA(0): NVIDIA GPU GeForce GTS 250M (GT215) at PCI:1:0:0 (GPU-0)
(--) May 08 19:06:54 NVIDIA(0): Memory: 1048576 kBytes
(--) May 08 19:06:54 NVIDIA(0): VideoBIOS: 70.15.0b.00.00
(II) May 08 19:06:54 NVIDIA(0): Detected PCI Express Link width: 16X
(--) May 08 19:06:54 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) May 08 19:06:54 NVIDIA(0): Connected display device(s) on GeForce GTS 250M at PCI:1:0:0:
(--) May 08 19:06:54 NVIDIA(0):     none
(EE) May 08 19:06:54 NVIDIA(0): No display devices found for this X screen.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Every single time for the last week and a half.

Stuff I've tried:

* Using the xorg-edgers ppa packages
* The upstream .run file from nvidia
* Setting a custom modeline
* Extracting the EDID information from the Windows installation and calling it in xorg.conf
* Turning off UseEDID altogether
* A bunch of other stuff, honestly it's all starting to blur together now

Versions of Ubuntu I've tried:

* Kubuntu 10.04, 64 and 32 bit
* Ubuntu 10.04, 64 bit
* Kubuntu 9.10, 64 and 32 bit

Attached are the latest iterations of my /var/log/Xorg.0.log and /etc/X11/xorg.conf. If there's anything else I could provide, just ask. Any help would be so very much appreciated. Seriously, this is driving me to drink.

---

### Post by TeeAhr1 on 2010-05-10
*bump

---

### Post by pauloricardomg on 2010-05-10
Hey,

I was having exactly the same problem (with a vaio vpcf11c5e), and solved with the EDID workaround.

I followed exactly these instructions: [http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

(used the softMCCS program to extract the EDID from windows 7)

I'm using ubuntu 10.04 amd64, kernel 2.6.32-22-generic.

Cheers,

Paulo

---

### Post by TeeAhr1 on 2010-05-10
Hot damn, mark it SOLVED! I had previously tried to extract an EDID from the Windows partition, but I had saved it as a *.raw file, and didn't include the "ConnectedMonitor" line. This totally worked! W00T!!!!!11!eleven!

Seriously, you have made my entire last two weeks totally worthwhile. I cannot thank you enough!

EDIT
---

For the sake of anyone finding this post through Google, here's the fix.

0. Not have deleted the Windows 7 installation that the machine shipped with (not too many times do I find myself saying anything like that, but there ya go)
1. Using [softMCCS]("http://www.entechtaiwan.com/lib/softmccs.shtm"), save the EDID from Windows 7 as edid.bin (it is IMPORTANT that you save this as a .bin file, .raw did not work for me). Save this to a thumb drive.
2. Boot Ubuntu to the recovery console, and save the edid.bin file in /etc/X11 (or wherever, but I found this to be convenient)
3. Add the following to the "Device" section of /etc/X11/xorg.conf:
```

"Option" "ConnectedMonitor" "DFP-0"
"Option" "CustomEDID" "DFP-0:/etct/X11/edid.bin"
```
4. Reboot. You're all set.

Thanks again, Paulo.

---

### Post by b00ey on 2010-09-29
Im going crazy here. How do I download this SoftMCCS ? There isnt a link on the site.. is it just me ?

---

### Post by elite1967 on 2010-11-13
> **b00ey said:**
> Im going crazy here. How do I download this SoftMCCS ? There isnt a link on the site.. is it just me ?

Hi, 
check here:
[http://www.entechtaiwan.com/lib/softmccs.shtm](http://www.entechtaiwan.com/lib/softmccs.shtm)

bye

---

### Post by ronninlee on 2010-11-23
I have uninstalled the windows 7. Is the edid.bin the same for all B500 (with GeForce GTS 250M)? 
if so, can somebody share yours for me?  thank you ahead.

---

### Post by Lady_Chloe on 2011-04-17
I have run into a similar problem. Unfortunately, dumping the EDID and loading it did not help.
nVidia drivers find the GT218 chip but say:

(WW) NVIDIA(GPU-0): Invalid ConnectedMonitor request; request was for 'DFP-0', but
(WW) NVIDIA(GPU-0): the valid display devices are ''

and of course
(EE) NVIDIA(0): No display devices found for this X screen.


The problem is probably that the intel card is still given the DFP-0 connector and nVidia cannot see it. I tried using the acpi_call but I get:
acpi_call: Cannot get handle: Error: AE_NOT_FOUND

The test script for acpi_call fails at all calls! Please help!

---

### Post by tvaughan on 2011-05-10
Yeah, these instructions helped a lot. Thanks! While I can now start X without errors (on a brand new natty installation) using nvidia-current, GDM starts up but there is no video output - just a blank/black screen. I can hear the "drumroll" so I know that GDM has started. That, plus there are no error messages in Xorg.x.log and gdm.log. Clues?

---

### Post by breenmachine on 2011-05-13
Same problem as tvaughan right now...

---

### Post by porcho on 2012-11-04
Thanks a lot, pauloricardomg and TeeAhr1! Following your instructions, I was able to solve the problem I was facing while loading the nvidia driver for my GeForce GT 440 in Ubuntu 11.04. I'd just like to add two things:

1) I couldn't get SoftMCCS to work (it didn't recognize my monitor), so I used [Phoenix EDID Designer]("http://downloads.yahoo.com/software/windows-web-tools-phoenix-edid-designer-s21726") instead.

2) Phoenix EDID only exports to raw format. I haven't had any problems with it so far.

Once again, thank you all!

---

