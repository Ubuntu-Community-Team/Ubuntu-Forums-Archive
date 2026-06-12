---
title: "Slow performance on 9.04"
date: 2009-08-18
forum: General Help
---

### Post by kenny99 on 2009-08-18
Hi, I recently installed 9.04 and now dual boot it with Vista on my work computer. I also adding some extra RAM at the same time and System Monitor shows 3.2GB of RAM available for my Dell Vostro (which has Intel Core Duo processor).

Strangely, Ubuntu is running pretty slowly despite the RAM upgrade. I am not running excessively resource intensive applications (apart from maybe Firefox with lots of web dev addons). I have Ubuntu 8.10 on my laptop at home with 3GB memory and it runs smoothly, so I'm not sure why I have the performance problem here. 

I boot Ubuntu and Vista from 2 separate drives, both of which have around 60GB of space available. I'm not sure what the issue could be here, if anyone could help that would be great. If you need more specific info then please let me know...

---

### Post by tgalati4 on 2009-08-18
Go through dmesg and cut-and-paste any errors/interesting items that you find.

dmesg | more

If you're not seeing a full 4 GB of RAM in ubuntu, then you are not running 64-bit.  I have found that 64-bit runs a little faster than 32-bit on Pentium D machines (dual-core).  

Of course, there could be some bottlenecks in the Core Duo chip that were quickly fixed when Core2Duo came out.

If it's just slow firefox performance, then run it in a ramdisk:

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm)

---

### Post by kenny99 on 2009-08-18
@tgalati4, thanks for the reply. Hmm, dmesg doesn't throw up anything obvious although there is a lot to digest so hopefully i've not missed something crucial, plus my system is slow even without firefox running so it's not specifically that (although i will look into the link you provided). I was previously running netbeans IDE which i thought was the problem, then i binned that, then it looked like firefox was the problem, but even without those two apps running it seems Gnome on 9.04 is just running really slow on my work PC.

As you say, I'm not seeing the full 4GB of RAM on 32 bit, but with 3.2 i shouldn't be experiencing the performance hit i'm getting at the moment. Still pretty new to Linux, so apologies in advance for over reliance on probably basic info...

---

### Post by tgalati4 on 2009-08-18
Post a summary of your system specs:

cat /proc/cpuinfo

and bogomips:

dmesg | grep BogoMIPS

and

lshw

lspci

You can cut it down somewhat, but we need to know what hardware you are running to determine what's causing the problem.

---

### Post by kenny99 on 2009-08-19
thanks again tgalati4, here's the output...

cat /proc/cpuinfo
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping	: 13
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4389.00
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping	: 13
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 4388.96
clflush size	: 64
power management:

```

dmesg | grep BogoMIPS
```
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.00 BogoMIPS (lpj=8778000)
[    0.004000] Calibrating delay using timer specific routine.. 4388.96 BogoMIPS (lpj=8777923)
[    0.420037] Total of 2 processors activated (8777.96 BogoMIPS).

```

lshw
```
nicky-desktop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3266MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:1d:09:77:58:3f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 ip=192.168.0.20 latency=0 module=e1000e multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:cf:b7:7b:87:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

lspci
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)

```

---

### Post by matthewbpt on 2009-08-19
Hmm it appears you have an Intel Graphics chip, this may be why. There was a regression in performance with intel graphics in jaunty, see this thread [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
That might be the issue but I'm not sure.

---

### Post by Sk00maKing on 2009-08-19
Is there some kind of speedstep technology enabled on this machine? The cpu speed displayed is 1200 mhz. Maybe it is working abnormaly on your OS... Also, if you have 4 gigs of ram, i would suggect to verify if the motherboard supports it and install a 64bit version.

Sk00m.

---

### Post by Sk00maKing on 2009-08-19
You could also run a diag from the manufacturer of the hard drive that boots linux.

Sk00m.

---

### Post by tgalati4 on 2009-08-19
Agreed.  You should try the 64-bit version of either Intrepid (going back a version) or be daring and look for a 64-bit version of Koala.

Save your critical files.  And reinstall a different version of Ubuntu, or a different distro say Fedora or OpenSUSE.  Ubuntu should fly on your machine.  You have a Core2Duo not CoreDuo.  And yes, it seems to be running slower, perhaps you have on-demand turned on which throttles the cpu speed.

lsmod

This will list the kernel modules that you have loaded.  Look for acpi and cpufreq modules.

---

### Post by kenny99 on 2009-08-19
Thanks for all the help guys. Yep, looks like my Intel Graphics card is causing the issue with Jaunty. So I have the option of following the fix for that, or going back to Intrepid or going all out for a different distro. 

Re the 64 bit option, is there not going to be an issue with 64 bit versions of applications not being available? It looks like this used to a be a bit of a problem.  

Also very tempted by another distro. I have ubuntu on my own laptop at home and would like to have experience of a distro which forces me to use the command line a lot more, as a bit of a learning experience.

---

### Post by TRG1 on 2009-08-19
I was here the other day getting help installing 9.04, basically as an experiment, on an older computer.  I just wanted to see what linux was all about.  The older computer is 9 yrs old running XP with 256Mb ram and a 733Mhz P3.  I run it with a bare bones version of XP and use it only for browsing with Google chrome.  It will go from off to surfing in less than a minute and browsing performance is not significantly different from my newer machines.  It seems like if linux is going to win people over then it needs to start up and outrun windows.  In this particular case it ran slower than almost any windows machine I've ever had.  I am no geek, but I've had pc's since about 1982 and I've taken them completely apart and built them from scratch.  Trying to get ubuntu running was about as challenging a startup of anything I've ever seen and the performance was terrible once it was running.  I hate Msft as much as the next person, but if the linux world is going to complete it has got to offer something better than what I've seen.  I wish you all luck though.

---

### Post by matthewbpt on 2009-08-19
> I was here the other day getting help installing 9.04, basically as an experiment, on an older computer. I just wanted to see what linux was all about. The older computer is 9 yrs old running XP with 256Mb ram and a 733Mhz P3. I run it with a bare bones version of XP and use it only for browsing with Google chrome. It will go from off to surfing in less than a minute and browsing performance is not significantly different from my newer machines. It seems like if linux is going to win people over then it needs to start up and outrun windows. In this particular case it ran slower than almost any windows machine I've ever had. I am no geek, but I've had pc's since about 1982 and I've taken them completely apart and built them from scratch. Trying to get ubuntu running was about as challenging a startup of anything I've ever seen and the performance was terrible once it was running. I hate Msft as much as the next person, but if the linux world is going to complete it has got to offer something better than what I've seen. I wish you all luck though.
You tried to run the full Ubuntu on a 9 year old computer with 256 megs of ram! I'm quite sure thats bellow the system requirements. Remeber that xp came out about 4 years before Ubuntu... If you want to run linux on that machine you could use Damn Small Linux or Puppy Linux, which are specifically designed for low spec machines. Or at least try Xubuntu, an edition of Ubuntu with a smaller footprint (though that would still be pushing it). Don't come to us with tales of bad performance when you are trying it on a machine like that, Ubuntu is a modern OS.

---

### Post by TRG1 on 2009-08-19
I get the fact that my box is out of date, but as I pointed out it's still doing ok with XP which is still in very wide use.  Why should ubuntu be so demanding of hardware; what's the point in that?  It seems to me one of the biggest problems with windows is all of the crap they hang on it and after you run it for a while it becomes slow due to all the misc junk it's running.  Why try to be like windows? But, I will try it on some more up to date hardware and report back.

---

