---
title: "Aspire One 521 Athlon II Neo Procesor K125 installation problem"
date: 2010-08-09
forum: General Help
---

### Post by utileria on 2010-08-09
Trying to install 10.04 and remix 10.04  in model AO521-3165 Aspire One 521 Athlon II Neo Procesor K125  gives an installation failure. (Tested in several AO521 giving the same result all of them with the latest bios update)

a) The first message: Disabling IRQ # 18

b) 10.04 in mode installing without modification gets into a 3 sound loop and then halts completely.

c) remix in mode installing without modification gets into the gnome screen but the keyboard is completely dead.

d) Installing both of them in the hard disk can partition hard disk but then the system asks the name and password and again the keyboard is dead.

Here is another message trying to install BackTrack4R1 giving maybe more clues:

[Firmware bug] PCI MMConfig at (mem 0xe0000000 - 0xe03fffff not reserved in ACPI motherboard resources
i8042.C: Can´t read CTR while initializing i8042
irq18 nobody cared (try booting with the "irqpool" option)
Disabling IRQ #18

e) The same result with Open Suse.

Help me with this technical issue.

Thank you very much!

---

### Post by dino99 on 2010-08-09
try to boot by adding [COLOR="Blue"]irqpoll[/COLOR] on the boot line

---

### Post by utileria on 2010-08-09
> **dino99 said:**
> try to boot by adding [COLOR=Blue]irqpoll[/COLOR] on the boot line

Adding irqpoll gives the same result and the message:

[31.000154] shpchp 0000:00:01.0: Cannot reserve MMIO region

---

### Post by dino99 on 2010-08-09
so try with other setting: 

either: irqpoll, nomodeset, noacpi, nolapic, noapic

*** boot without quiet & splash, to see comments and warning while booting, that will help to know whats wrong

---

### Post by utileria on 2010-08-09
> **dino99 said:**
> so try with other setting: 

either: irqpoll, nomodeset, noacpi, nolapic, noapic

*** boot without quiet & splash, to see comments and warning while booting, that will help to know whats wrong


I tried all the available settings: Expert mode, acpi=off, noapic, nolapic, edd=on, nodmraid, nomodreset, and all of them give the same result.

---

### Post by Snyder.4000 on 2010-08-15
I have the same problem, first i try to install Ubuntu 10.04 netbook edition and the keyboard and touchpad were dead... i try again whit jolicloud and it was the same.
Can anyone help us? :confused:

---

### Post by strange1712 on 2010-08-17
Exactly the same problem here, well described. Same problem with openSuse (totally fail) and even gparted live...
Installed Ubuntu by choosing install instead of try, using USB Keyboard and USB Mouse, and then Ubuntu Netbook Remix and neither detected the keyboard once in graphic mode (GRUB does). In the last one I updated/Upgraded the whole system (Kernel included) and still the keyboard and PAD was not recognized. I successfully installed ATI Catalyst driver from repositories, and 3D acceleration seems to work right, but the entire system still feels extremely slow, though GLXGEARS looked smooth. 
Wifi is working, and even speakers, but LAN is not working. Didn't try the SD reader. Seems like this platform definitely doesn't like LINUX at all...

Don't know if this could be related:
[http://en.wikipedia.org/wiki/AMD_800_chipset_series#Southbridge_issues.28SB8x0.29](http://en.wikipedia.org/wiki/AMD_800_chipset_series#Southbridge_issues.28SB8x0.29)
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=73472a46b5b28116b145fb5fc05242c1aa8e1461](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=73472a46b5b28116b145fb5fc05242c1aa8e1461)

Frustrating...

---

### Post by benster21 on 2010-08-17
I have the same problem with my gateway lt2207h (same cpu and chipset).

I opened a case on ubuntu.com launchpad and this is not going forward. For now, I installed ubuntu via virtualbox in windows but it is kind of annoying. 

[https://answers.launchpad.net/ubuntu/+question/121218](https://answers.launchpad.net/ubuntu/+question/121218)

---

### Post by utileria on 2010-08-17
> **benster21 said:**
> I have the same problem with my gateway lt2207h (same cpu and chipset).

I opened a case on ubuntu.com launchpad and this is not going forward. For now, I installed ubuntu via virtualbox in windows but it is kind of annoying. 

[https://answers.launchpad.net/ubuntu/+question/121218](https://answers.launchpad.net/ubuntu/+question/121218)

I found this for the wired ethernet card (not detected). I haven´t tested it yet. I am afraid that trying this option would affect the wireless card (at least it seems stable and without any issue).

[http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

I also tried to upgrade to 10.10 alpha 3 (it seems that the new kernel will recognize the wired ethernet card) but it does not reboot (maybe a bug).

The microphone is working very bad, nobody can hear my conversations in Skype or Gizmo5.

I will try to test again the bluetooth microphone function, maybe the handsfree headset is out of order. 

Any other technical issue I will post it. 

Thank you for your help guys!

---

### Post by KellyLSB on 2010-08-22
I installed UNR of sd card works great.

---

### Post by keibee on 2010-08-31
> **utileria said:**
> 

The microphone is working very bad, nobody can hear my conversations in Skype or Gizmo5.


I got that fixed by installing pulseaudio, set internal analog stereo channels: left 0% and right 70%.  Mic now works perfectly.

LAN got enabled by downloading the [_driver_]("http://partner.atheros.com/Drivers.aspx") and compiling them for the kernel I am using.  I have to redo this for every new kernel...

Still looking for a solution to fix the battery detection (ACPI issue).  There seems to be a [_kernel patch for Acer Timeline_]("http://ubuntuforums.org/showthread.php?t=1495123&page=4") machines which suffer from the same issue.  I do not really like to apply that patch though.  I am eagerly awaiting a solution to the ACPI problem.




Keibee

---

### Post by utileria on 2010-09-10
The keyboard and mouse track are now working!

Update to the latest Aspire One 521´s bios 1.08 (BIOS 	Acer 	Fixes Keyboard issue in Linux. 	1.08 	2.3 MB 	2010/09/06

[http://us.acer.com/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012](http://us.acer.com/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012)

Let us know about the other missing features.

Thank you guys.

---

### Post by thedud on 2010-09-10
I have tested this bios update and it does indeed fix the mouse/keyboard issue.
I am glad that Acer takes pride in its product and is willing to take into account that not everyone likes to use Windows on their machines.

Cheers!

---

### Post by yakoob on 2010-09-12
I have an issue with the Fn keys. Trying to change the brightness for example, the system hangs. Is there any solution for the missing functionality of the special function keys?

---

### Post by keibee on 2010-09-13
> **yakoob said:**
> I have an issue with the Fn keys. Trying to change the brightness for example, the system hangs. Is there any solution for the missing functionality of the special function keys?

I've solved that one by installing the ATI drivers, just search "ati" in the ubuntu software center application which you will find in the system menu.  I have installed the fglrx stuff which improved a lot of things and made my Fn keys work for brightness and audio. The other keys don't do much.
  
Still looking to get the battery indicator working.  Really annoying...

K.

---

### Post by Ouel on 2010-09-15
Could you please post your xorg.conf ...
im trying to install the ati catalyst but i got a strange problem. 

how did you fix the sound bug ?

(using fedora 13 with acpi=off on gateway lt 22)

ty

---

### Post by keibee on 2010-09-16
> **Ouel said:**
> Could you please post your xorg.conf ...
im trying to install the ati catalyst but i got a strange problem. 

how did you fix the sound bug ?

(using fedora 13 with acpi=off on gateway lt 22)

ty

xorg.conf :


Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


See previous posts on audio (10th of August) in this thread.  There is still the issue of the speakers which stay on when headphones are connected.  Haven't found a soluton for this yet.

It looks like upgrading to kernel 2.6.35 should solve some of the issues (network / battery status).  I would personally stay with Lucid for a while and upgrade to 2.6.35 instead of going to Maverick (10.10) as the first beta test report for the aspire one 521 is not positive.

K.

---

### Post by benster21 on 2010-10-03
I just wanted to add that the latest bios update from Acer Aspire One 521 will fix the problem on the Gateway LT2207H (same machine). The problem related to the keyboard and mouse issue.

For those who are afraid of trying an Acer's bios on a Gateway machine, I just want you to know that Gateway was bought by Acer and that I also did a binary comparison of the 1.03 bios of both companies and this is an exact match. In my case, every computer hardware in the computer is exactly the same. DO NOT try this if you don't have the EXACT same specs.

---

### Post by keibee on 2010-10-28
> **keibee said:**
> There is still the issue of the speakers which stay on when headphones are connected.  Haven't found a soluton for this yet.

Well, if finally got the audio issue fully solved, albeit after upgrading to 10.10 - so I do not know whether this works in 10.04...  please let us know if it does work in older versions.

I have added the following line to the end of the /etc/modprobe.d/alsa-base.conf file:
ptions snd-hda-intel model=thinkpad


Found via: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040)


BTW, I would not recommend upgrading to 10.10 as the new Unity interface (through Mutter) consumes by default 20-30% of the total available memory, the ATI display driver (fglrx) is full of render bugs and I can no longer watch HD content (720p) at full frame rate.  The main battery status issue is still not solved so I am currently worse off.  :(

Keibee

---

### Post by Supergnu on 2011-01-03
So what does not work up to yet?

Oh yes, here is a kernel patch to fix the battery detection bug: [https://bugzilla.kernel.org/attachment.cgi?id=25890](https://bugzilla.kernel.org/attachment.cgi?id=25890)
precompiled kernel (32bit): [http://dl.dropbox.com/u/1744425/linux-image-2.6.35.4%2Bao521_2.6.35.4%2Bao521-10.00.Custom_i386.deb](http://dl.dropbox.com/u/1744425/linux-image-2.6.35.4%2Bao521_2.6.35.4%2Bao521-10.00.Custom_i386.deb)
and headers: [http://dl.dropbox.com/u/1744425/linux-headers-2.6.35.4%2Bao521_2.6.35.4%2Bao521-10.00.Custom_i386.deb](http://dl.dropbox.com/u/1744425/linux-headers-2.6.35.4%2Bao521_2.6.35.4%2Bao521-10.00.Custom_i386.deb)

If you have problems with suspend/hibernation you can replace acpi with apmd and cpufreqd

I hope this helps

---

### Post by kanoconk on 2011-03-28
Hi!
I have the same problem with the BIOS but I can´t execute de upgrade for this AO521. ¿How can I upgrade the BIOS?, ¿recomendations?
Thanks

---

