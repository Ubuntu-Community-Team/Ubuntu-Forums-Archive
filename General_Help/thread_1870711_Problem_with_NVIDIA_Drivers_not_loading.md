---
title: "Problem with NVIDIA Drivers not loading"
date: 2011-10-27
forum: General Help
---

### Post by Tony Flury on 2011-10-27
running ubuntu 10.04 on a brand new laptop - and the NVIDIA driver wont load : 
kern.log extract :
```

Oct 27 21:39:30 laptop kernel: [   26.235535] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:30 laptop kernel: [   26.236602] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:30 laptop kernel: [   26.236609] NVRM: rm_init_adapter(0) failed
Oct 27 21:39:31 laptop kernel: [   26.334392] device eth0 entered promiscuous mode
Oct 27 21:39:31 laptop kernel: [   26.613761] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:31 laptop kernel: [   26.614828] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:31 laptop kernel: [   26.614835] NVRM: rm_init_adapter(0) failed
Oct 27 21:39:31 laptop kernel: [   26.852552] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:31 laptop kernel: [   26.853582] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:31 laptop kernel: [   26.853589] NVRM: rm_init_adapter(0) failed
Oct 27 21:39:31 laptop kernel: [   27.025660] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:31 laptop kernel: [   27.026720] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:31 laptop kernel: [   27.026727] NVRM: rm_init_adapter(0) failed
Oct 27 21:39:31 laptop kernel: [   27.190123] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:31 laptop kernel: [   27.191231] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:31 laptop kernel: [   27.191237] NVRM: rm_init_adapter(0) failed
Oct 27 21:39:32 laptop kernel: [   27.362859] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:32 laptop kernel: [   27.363888] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:32 laptop kernel: [   27.363895] NVRM: rm_init_adapter(0) failed
Oct 27 21:39:32 laptop kernel: [   27.599613] NVRM: failed to copy vbios to system memory.
Oct 27 21:39:32 laptop kernel: [   27.600644] NVRM: RmInitAdapter failed! (0x30:0xffffffff:868)
Oct 27 21:39:32 laptop kernel: [   27.600651] NVRM: rm_init_adapter(0) failed

```

Xorg.log extract
```

(**) Oct 27 22:10:07 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 27 22:10:07 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 27 22:10:07 NVIDIA(0):     enabled.
(EE) Oct 27 22:10:07 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) Oct 27 22:10:07 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Oct 27 22:10:07 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Oct 27 22:10:07 NVIDIA(0):     README for additional information.
(EE) Oct 27 22:10:07 NVIDIA(0): Failed to initialize the NVIDIA graphics device!

```

lspci extract
```

01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

```

lshw extract
```


           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:92000000-92ffffff memory:80000000-8fffffff(prefetchable) memory:90000000-91ffffff(prefetchable) ioport:4000(size=128) memory:93080000-930fffff(prefetchable)

```


Can anyone give me some pointers - as having to run this laptop is low resolution mode is annoying :(

---

### Post by 23dornot23d on 2011-10-27
No idea what your computer is ..... or the graphics card other than its Nvidia .....

> 
NVIDIA graphics device PCI ....... Failed .....

01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
So based on that .....

Here is what I do when my Nvidia Card does not work .... mine is quite old though and you
say you have a new computer .... so that narrows it down .... :confused:

First ...... run synaptic .......

then search for Nvidia ...... remove everything that starts with Nvidia

now check which kernel you are running ....... make sure the headers are there for the version you have  .....

Now you could try these commands below or wait for someone that knows what they
are doing ......

sudo rm /etc/X11/xorg.conf

sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install nvidia-settings

sudo aptitude install nvidia-current

watch and make sure it installs correctly with no [COLOR=Red]**FAIL **[/COLOR]markers anywhere ....

re-create xorg.conf (I think its ... )

[sudo **nvidia-xconfig**]("http://linux.die.net/man/1/nvidia-xconfig")

reboot cross your fingers and hope for the best ....... :D

if this does not work .... add some more information .... for the next person to try .....

Computer ?

[COLOR=Blue]mine is a 
Acer 7730 zg[/COLOR]

Graphics Card ? 

[COLOR=Blue]type (example - mine is a PCIe Nvidia [**9300 GS**]("http://en.wikipedia.org/wiki/GeForce_9_Series")) [/COLOR]

Current Kernel ? 

uname -a 

[COLOR=Blue]Linux keith-Aspire-7730ZG 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
[/COLOR]

[COLOR=Black]Best of luck ....[/COLOR]

---

### Post by Tony Flury on 2011-10-28
bios info :
```

tony@laptop:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: INSYDE
	Version: 1.71
	Release Date: 04/19/2011
	ROM Size: 2560 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 71.240

Handle 0x000D, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 4
		en|US|iso8859-1
		fr|CA|iso8859-1
		ja|JP|unicode
		zh|TW|unicode
	Currently Installed Language: en|US|iso8859-1

```

Kernel info : 

```

Linux laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

```

The nvidia driver is nvidia current - that has installed ok. The error message continues as above.

The laptop is a custom built : Enigma III 540 from pcspecialists

---

### Post by SwitchDK on 2011-10-28
Hi Tony,

When I have had problems in the past with the nvidia drivers that are in the software repository I have used Nvidia's own installation package. The package has come a long way from the early version 100-days so the install script is fully automatic.

Basically, make a backup of /etc/X11/xorg.conf, remove everything on your machine that is nvidia related like 3dornot23d suggested and then install the nvidia drivers from Nvidia's website (the driver package is also a installation script).

I hope it works for you.

Your can find a rough guide on how to do it [here]("http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/")

---

### Post by 23dornot23d on 2011-10-28
Have you tried Ubuntu 10.10 on it ...... download and try the liveCD and see if the same problem occurs ......

After reading a few threads ...... seems that a later kernel helped for some people  .....

First try what SwitchDK as proposed ...... 

the [Nvidia drivers for the 540 <<< could be this one .... you need to check though .....]("http://www.nvidia.com/object/linux-display-ia32-270.41.06-driver.html")

thats for the 32 bit which your kernel is at the moment ...

Linux laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 [COLOR=Red]**i686**[/COLOR] GNU/Linux

Another Option

[COLOR=Blue]**If it was me I would go to [Ubuntu 64 bit 10.10]("http://cdimage.ubuntu.com/releases/10.10/release/") .. if your computer supports 64 bit .... and add the [Nvidia 64bit drivers]("http://www.nvidia.com/object/linux-display-amd64-275.19-driver.html")**[/COLOR] <<< check that this is the right driver for your system though

---

### Post by Tony Flury on 2011-10-29
> **SwitchDK said:**
> Hi Tony,

When I have had problems in the past with the nvidia drivers that are in the software repository I have used Nvidia's own installation package. The package has come a long way from the early version 100-days so the install script is fully automatic.

Basically, make a backup of /etc/X11/xorg.conf, remove everything on your machine that is nvidia related like 3dornot23d suggested and then install the nvidia drivers from Nvidia's website (the driver package is also a installation script).

I hope it works for you.

Your can find a rough guide on how to do it [here]("http://www.omgubuntu.co.uk/2010/02/how-to-install-nvidia-drivers-manually-in-ubuntu/")

That worked - fantastic - thank you :-)

:popcorn:

---

