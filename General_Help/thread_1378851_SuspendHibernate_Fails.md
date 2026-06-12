---
title: "Suspend/Hibernate Fails"
date: 2010-01-11
forum: General Help
---

### Post by whinis on 2010-01-11
I am using a Asus g51j-a1 laptop with Ubuntu 9.10.

uname -a "Linux john-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
"
If I try to suspend or hibernate my laptop it seems to finish just fine going to a black scrrne, but then immediately it seems to reboot and freeze with a blinking cursor. I have searched and have been unable to find a fix. Logs seem to suggest that it successfully suspend or hibernates but then immediately tries to resume.

Upon reviewing logs for sleep and kernel it goes immediately from sleep to try to reawaken

"Jan  4 14:45:43 john-laptop kernel: [ 1996.990994] CPU 7 is now offline
Jan  4 14:45:43 john-laptop kernel: [ 1996.990998] SMP alternatives: switching to UP code
Jan  4 14:45:43 john-laptop kernel: [ 1996.996159] CPU0 attaching NULL sched-domain.
Jan  4 14:45:43 john-laptop kernel: [ 1996.996162] CPU7 attaching NULL sched-domain.
Jan  4 14:45:43 john-laptop kernel: [ 1996.996170] CPU0 attaching NULL sched-domain.
Jan  4 14:45:43 john-laptop kernel: [ 1996.996327] CPU7 is down
Jan  4 14:45:43 john-laptop kernel: [ 1996.996364] Extended CMOS year: 2000
Jan  4 14:45:43 john-laptop kernel: [ 1996.996443] PM: Creating hibernation image: 
Jan  4 14:45:43 john-laptop kernel: [ 1997.106891] PM: Need to copy 125651 pages
Jan  4 14:45:43 john-laptop kernel: [ 1997.106893] PM: Normal pages needed: 125651 + 1024 + 80, available pages: 920135
Jan  4 14:45:43 john-laptop kernel: [   15.328751] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan  4 14:45:43 john-laptop kernel: [   15.329474] PM: Restoring platform NVS memory
Jan  4 14:45:43 john-laptop kernel: [   15.333268] CPU0: Thermal LVT vector (0xfa) already installed
Jan  4 14:45:43 john-laptop kernel: [   15.333324] Extended CMOS year: 2000
Jan  4 14:45:43 john-laptop kernel: [   15.333351] Enabling non-boot CPUs ...
Jan  4 14:45:43 john-laptop kernel: [   15.333515] SMP alternatives: switching to SMP code
Jan  4 14:45:43 john-laptop kernel: [   15.338472] Booting processor 1 APIC 0x2 ip 0x6000
Jan  4 14:45:43 john-laptop kernel: [   15.348715] Initializing CPU#1"

---

### Post by tbranham on 2010-03-06
Hi whinis,

I have the same laptop (well, the x1 version...) and I can't seem to get mine to suspend either.

I've tried all of the most common suggested fixes:
* Adjusting 'acpi_sleep' in /etc/default/grub
* Twiddling POST_VIDEO in /etc/default/acpi-support
* Twiddling SAVE_VIDEO_PCI_STATE in /etc/default/acpi-support
* Disabling Compiz
* Adding 'btusb' to the list of modules to disable in /etc/default/acpi-support
* Hoping that it will go away on its own
* Throwing salt over my shoulder
* and others...

all to no avail. My symptoms are *almost* exactly the same -- it seems to try to suspend, but it immediately tries (and fails) to wake, giving me the Black Screen of Death (no blinking cursor for me, which seems to be the only difference). The logs indicate a successful suspend, and an immediate wake. Sifting through dmesg doesn't provide much useful info on what is triggering the wake.

Anybody out there think they can help us tackle this?

Much appreciated,
Travis

---

### Post by tbranham on 2010-03-06
Oops, I just realized that I didn't give you all much to go on ;)

lspci:
```

tbranham@shrike:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0cb1 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be4 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
06:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
06:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
06:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
07:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

FYI, the video card is the NVIDIA GeForce GTS 360M, which doesn't seem to have any major issues using the current NVIDIA drivers. Additionally, I went back to the VESA driver: no joy.

lsusb:
```

tbranham@shrike:~$ lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:a122 Suyin Corp. 
Bus 001 Device 003: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

/proc/acpi/wakeup:
```

tbranham@shrike:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P1	  S4	 disabled  pci:0000:00:1e.0
HDEF	  S4	 disabled  pci:0000:00:1b.0
PEG4	  S4	 disabled  
PEG5	  S4	 disabled  
PEG6	  S4	 disabled  
EHC0	  S3	 disabled  pci:0000:00:1d.0
USB0	  S3	 disabled  
USB1	  S3	 disabled  
USB2	  S3	 disabled  
USB3	  S3	 disabled  
EHC1	  S3	 disabled  pci:0000:00:1a.0
USB4	  S3	 disabled  
USB5	  S3	 disabled  
USB6	  S3	 disabled  
RP01	  S4	 disabled  pci:0000:00:1c.0
RP02	  S4	 disabled  pci:0000:00:1c.1
WLAN	  S3	 disabled  pci:0000:03:00.0
RP04	  S4	 disabled  
RP05	  S4	 disabled  pci:0000:00:1c.4
RP06	  S4	 disabled  pci:0000:00:1c.5
GLAN	  S4	 disabled  pci:0000:07:00.0
RP07	  S4	 disabled  
RP08	  S4	 disabled  
PEG3	  S4	 disabled  pci:0000:00:03.0
RP03	  S3	 disabled  pci:0000:00:1c.2
SLPB	  S4	*enabled   

```

If you think anything else is relevant, let me know.
-Travis

---

### Post by rdelcueto on 2010-04-02
Hi everyone,
I own an Asus G51J since last October, and ever since I've been struggling to get Suspension to work under Linux, but until today I've been unsuccessful. I've already mail the Asus support, and they told me Linux is not a supported OS for this model, so they couldn't help me here. (What a surprise! :mad:)

I've tried recent Kernels as well as the the uswsusp alternative  modules, but the result is always the same, a black screen with a blinking cursor and the harddrive led on. While in this state, the laptop won't respond to any command, not even the Magic SysRq Keys, the only option is to do a hard shutdown by holding the power button. One interesting fact is that, through a "Kill A Watt" device I've seen it's pulling 85 watts, which is the usual energy drain while the CPU usage is at 100% (Maybe some sort of spinlock). So as far as suspension goes, it appears to be completely broken.

Hibernating is a different story, using the uswsusp modules I've had varying result; sometimes it won't hibernate, sometimes it won't resume, sometimes it works but always with side effects, such as having unusable idling cores after resuming. I also had to change the uswsusp.conf shutdown method to "shutdown" in order to get the laptop to shutdown after creating and saving the snapshot. Hybrid methods don't work at all, same results as when trying to suspend, so maybe a part of the ACPI support is badly broken, and this points out why in won't suspend in the first place. :?

What I recommend is using the TuxOnIce modules, both the hibernation and resuming processes seemed faster than uswsusp, and I've found them to be way more reliable, as it has never failed to hibernate or resume.

I'm currently trying Lucid Lynx's Beta, suspension is still broken, and I haven't been able to get TuxOnIce to work. =/

Note: I found this post on a ArchLinux forum, with an apparent solution, but it didn't work for me.
[http://bbs.archlinux.org/viewtopic.php?pid=692927](http://bbs.archlinux.org/viewtopic.php?pid=692927)

---

### Post by HermanAB on 2010-04-02
Howdy,

What is the size of your swap partition?  It has to be at least two times the size of the RAM for suspend to work.

---

### Post by adamantoi on 2010-04-02
> **HermanAB said:**
> Howdy,

What is the size of your swap partition?  It has to be at least two times the size of the RAM for suspend to work.
so linux use swap partition to store suspend data?

---

### Post by wadam on 2010-04-12
> **HermanAB said:**
> Howdy,
 
What is the size of your swap partition? It has to be at least two times the size of the RAM for suspend to work.
 
I am having a similar problem to Rdelcueto using Lucid Beta 2.  When I installed it, I had the installer use Ubuntu's default settings.  I am not currently in front of my computer, so I can't tell you how big my swap partition is.  But I'm pretty sure that it isn't twice my amount of RAM.  If I were to use gparted or some such to resize the partition, are you suggesting that that would help?  And if that is in fact the case, is this a problem with the Ubuntu Installer?

---

### Post by hsu on 2010-05-04
I have 15GB of swap (6GB ram), and hibernate used to work in Karmic, but no longer working in Lucid.

---

### Post by trigg on 2010-06-05
Ping

Is this thread still alive?  I have the issue as well and have not been able to find a solution I've tried the solution posted for the G60JX, but to no avail.

---

### Post by makindue on 2010-06-28
Hello trigg, I hope that it is still alive. I am also having difficulty with it. I hope that we can resolve our problems as soon as possible. :D

---

### Post by Gratarian on 2010-09-25
> **hsu said:**
> I have 15GB of swap (6GB ram), and hibernate used to work in Karmic, but no longer working in Lucid.

It is helpful to see that it was working at one point and is no longer working. While there are probably a lot of difference (package wise) between these two. I might just install Karmic just to see it working.

---

### Post by hsu on 2010-09-25
I found John Dia's response in this thread fixed my problem:

[http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

also, gecka's patch below fixed keyboard backlight when suspending:

[http://ubuntuforums.org/showthread.php?t=1546748](http://ubuntuforums.org/showthread.php?t=1546748)

---

### Post by rdelcueto on 2011-10-18
After almost 2 years, I finally have my laptop's suspend ability working.

The solution should work with plenty ASUS laptops, more specifically the N71JQ and G51J families.

The issue's description and it's solution, can be found in this post:
[http://ubuntuforums.org/showpost.php?p=9180298&postcount=7](http://ubuntuforums.org/showpost.php?p=9180298&postcount=7)

What I tried, and solved my suspend/hibernating problem, was using the script described in the following blog:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

It works in the latest Ubuntu 11.10 (Oneiric Ocelot) Distribution.

Cheers

---

### Post by RogerDavis on 2012-05-17
Me too, on a desktop.  Never finishes the shutdown, use power off to kill it since the system thinks it's still working, start it again with power on, networking is turned off and have to sign in again.

---

