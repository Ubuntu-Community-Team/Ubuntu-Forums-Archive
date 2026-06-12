---
title: "Why Does 10.4 Take So Long To Boot-Up?"
date: 2010-05-02
forum: General Help
---

### Post by londonlad on 2010-05-02
hi all,

when i turn my laptop on, the screen goes blank with a single flashing cursor in the top left corner for about 10 secs, 10.4 is far slower to boot than 9.10 was............why? i thought 10.4 was meant to boot up quicker than 9.10? :(

---

### Post by dino99 on 2010-05-02
did you had grub1 installed ?

is grub2 installed on lucid mbr partition ?

sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by ankit singh on 2010-05-02
[http://ubuntuforums.org/showthread.php?p=9218536#post9218536](http://ubuntuforums.org/showthread.php?p=9218536#post9218536)
follow the instructions here.
It solved mine

---

### Post by londonlad on 2010-05-02
none of this has changed anything! im using an emachines e525 laptop running 10.4 only!

---

### Post by dino99 on 2010-05-02
any complaints into logs or .xsession-errors ?

---

### Post by londonlad on 2010-05-02
> **dino99 said:**
> any complaints into logs or .xsession-errors ?

no mate, nothing! is this a bug?

---

### Post by dino99 on 2010-05-02
you talked about boot, could it be an video issue ?

system admin hardware driver: activated ?

which one is installed ?

---

### Post by Ad@m on 2010-05-02
It is interesting that you say it does nothing for 10 seconds.

By default Ubuntu's grub timeout is 10 seconds.

sudo gedit /boot/grub/grub.cfg

Scroll down until you see the following lines,

> if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=[COLOR=Red]10[/COLOR]
fi
### END /etc/grub.d/00_header ###Edit the 10 to say 0 and see if it makes a difference.

---

### Post by londonlad on 2010-05-02
> **dino99 said:**
> you talked about boot, could it be an video issue ?

system admin hardware driver: activated ?

which one is installed ?


when i do system>administration>hardware drivers nothing shows! :(

[[IMG]http://img215.imageshack.us/img215/7384/screenshotrhi.png[/IMG]](http://img215.imageshack.us/i/screenshotrhi.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by londonlad on 2010-05-02
> **Ad@m said:**
> It is interesting that you say it does nothing for 10 seconds.

By default Ubuntu's grub timeout is 10 seconds.

sudo gedit /boot/grub/grub.cfg

Scroll down until you see the following lines,

Edit the 10 to say 0 and see if it makes a difference.


tried this, no diff, so i put it back to 10! :(

---

### Post by ankit singh on 2010-05-02
> **londonlad said:**
> no mate, nothing! is this a bug?


Yes this is a bug.

---

### Post by Ad@m on 2010-05-02
Can you post a link to the bug report please, thanks.

---

### Post by londonlad on 2010-05-02
> **Ad@m said:**
> Can you post a link to the bug report please, thanks.

ad@m, im asking if this is a bug mate! :lolflag:

---

### Post by dino99 on 2010-05-02
there is a problem #9, need to solve it

which graphic card and wihch is installed into synaptic ?

---

### Post by Ad@m on 2010-05-02
> **londonlad said:**
> ad@m, im asking if this is a bug mate! :lolflag:
> **ankit singh said:**
> Yes this is a bug.

Unless im not reading right, ankit was confirming your question hence my request.

---

### Post by ankit singh on 2010-05-02
here is the link

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

and also

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787)

---

### Post by londonlad on 2010-05-02
> **dino99 said:**
> there is a problem #9, need to solve it

which graphic card and wihch is installed into synaptic ?

no idea! i think my graphics card is a 'mobile 4'............?

---

### Post by dino99 on 2010-05-02
> **londonlad said:**
> no idea! i think my graphics card is a 'mobile 4'............?

that is the main question :P , into console: lshw

---

### Post by londonlad on 2010-05-02
> **dino99 said:**
> that is the main question :P , into console: lshw


???

---

### Post by londonlad on 2010-05-03
is this what you mean:

simonrogers@simonrogers-laptop:~$ lshw
WARNING: you should run this program as super-user.
simonrogers-laptop        
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1944MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU          900  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:90000000-903fffff memory:80000000-8fffffff(prefetchable) ioport:5120(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:93400000-934fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:96704400-967047ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:96700000-96703fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:4000(size=4096) memory:95700000-966fffff ioport:90400000(size=16777216)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:94600000-956fffff ioport:91400000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:2c:34:e1:27
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:94600000-9460ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:1000(size=8192) memory:93500000-945fffff ioport:92400000(size=16777216)
           *-network
                description: Ethernet interface
                product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c0
                serial: 00:23:5a:87:f8:c3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=81.96.80.68 latency=0 multicast=yes
                resources: irq:27 memory:93500000-9353ffff ioport:1000(size=128)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:5080(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5060(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:5040(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5020(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:96704000-967043ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: ICH9M/M-E 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:5118(size=8) ioport:5134(size=4) ioport:5110(size=8) ioport:5130(size=4) ioport:50f0(size=16) ioport:50e0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:96704800-967048ff ioport:5000(size=32)
        *-ide:1
             description: IDE interface
             product: ICH9M/M-E 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:5108(size=8) ioport:512c(size=4) ioport:5100(size=8) ioport:5128(size=4) ioport:50d0(size=16) ioport:50c0(size=16)
  *-scsi:0
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
simonrogers@simonrogers-laptop:~$

---

### Post by DomesDKG on 2010-05-03
There's a section on this in the FAQ, I've copied it for you here. I had the same problem and this fixed it.
5. Bootup/Plymouth. 
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013](https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013)

Graphical solution : [http://news.softpedia.com/news/How-t...4-140810.shtml](http://news.softpedia.com/news/How-t...4-140810.shtml)

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
Code:
gksu gedit /etc/default/grub
and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1680x1050 Save the file and run
Code:
sudo update-grub
The resolution chosen should be your monitors native resolution.

Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.
Code:
gksu gedit /etc/initramfs-tools/conf.d/splash
and add this option FRAMEBUFFER=y, save the file.
Then
Code:
sudo update-initramfs -u
Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the floppy in the bios. This has been reported as a fix to this. [https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712](https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712)

If the problem is plymouth not displaying, and a black screen from grub to gdm, this could be due to graphics drivers needing to be loaded quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787)

Plymouth is installed with 2 themes by default you can install more via synaptic.
To change themes this code is used.
Code:
sudo update-alternatives --config default.plymouth

---

### Post by londonlad on 2010-05-08
would somebody please help me with my issue, thankyou!

---

### Post by ankit singh on 2010-05-10
> **DomesDKG said:**
> There's a section on this in the FAQ, I've copied it for you here. I had the same problem and this fixed it.
5. Bootup/Plymouth. 
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013](https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013)

Graphical solution : [http://news.softpedia.com/news/How-t...4-140810.shtml](http://news.softpedia.com/news/How-t...4-140810.shtml)

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
Code:
gksu gedit /etc/default/grub
and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=write ur your monitor resolution here(eg:1400x900)
Save the file and run
Code:
sudo update-grub
The resolution chosen should be your monitors native resolution.

Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.
Code:
gksu gedit /etc/initramfs-tools/conf.d/splash
and add this option FRAMEBUFFER=y, save the file.
Then
Code:
sudo update-initramfs -u
Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the floppy in the bios. This has been reported as a fix to this. [https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712](https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712)

If the problem is plymouth not displaying, and a black screen from grub to gdm, this could be due to graphics drivers needing to be loaded quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787)

Plymouth is installed with 2 themes by default you can install more via synaptic.
To change themes this code is used.
Code:
sudo update-alternatives --config default.plymouth


have u done the above thing?, it should solve everything.
if not
paste ur log file content here

---

### Post by justinjedlawton on 2010-07-06
i have the same prblm w/ the same os 10.04 same laptop emachine E525
DOESanyone have an answer

---

### Post by Braik on 2010-07-06
Hi there,
 
I was wondering that this was the same issue I was having since last update (last week) of Lucid. The update (sorry I did not looked what was been updated, but I think the kernel was) asked me a reboot and after that my machine has get stucked with a _ cursor blinkkng, and nothing more, and this happened many times. But suddenly when I was trying to understand and repair this by booting without the "quiet splash" option all went good, and I did not see any clue about the problem.
 
After that I have some crashes that block my computer and some times I have to launch my computer twice to boot. Before this problem I had some problems with my (old ATI) graphic card that makes me think that this PLYMOUTH is the issue.
 
Any advices, or propositions for this ?
 
Thanks a lot in advance.

---

### Post by philinux on 2010-07-06
Double check with the General Help forum sticky,

---

### Post by Braik on 2010-07-06
That worked great, thanks folks. I reduced grub time as proposed, and made :
```
Other graphics card users may get a black screen with flashing cursor  and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.
Code:
gksu gedit /etc/initramfs-tools/conf.d/splash
and add this option FRAMEBUFFER=y, save the file.
Then
Code:
sudo update-initramfs -u
```
The splash screen came quickly even if start was maybe still little long but this is better

---

### Post by Strongman332 on 2010-07-06
mine hangs for 10 seconds as well, however after those 10 seconds it boots to the login prompt in 10 seconds, total 20 seconds much faster than 40 seconds for 9.10

---

### Post by jangozo on 2010-07-09
I tried the suggestions above but I'm stilling having this problem. I don't have nVidia, I've got a Dell Inspiron with integrated gfx card.

Anyone? :)

PS. Is there a log I can look at for this?

---

### Post by Braik on 2010-07-09
> **jangozo said:**
> I tried the suggestions above but I'm stilling having this problem. I don't have nVidia, I've got a Dell Inspiron with integrated gfx card.
 
Anyone? :)
 
PS. Is there a log I can look at for this?
 
Hi Jagonzo,
 
Me either I do not have an Nvidia card so I tried the second solution (instead of first) as you can see in my previous post and it works, have you read carefully all the topic?

---

### Post by browny74 on 2010-07-25
I have the same issue I am using 10.4 on a dell Inspiron E1505 and duel boot with windows vista I edited grub line........

 if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=[COLOR=Red]10[/COLOR]
fi
### END /etc/grub.d/00_header ### 			 		
..............................
 I set the second timeout line to 0 to see if that changed anything and it still takes 37 seconds before it shows splash screen. any help please .

---

### Post by wallpaper_thief on 2010-07-28
> **browny74 said:**
> I have the same issue I am using 10.4 on a dell Inspiron E1505 and duel boot with windows vista I edited grub line........

 if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=[COLOR=Red]10[/COLOR]
fi
### END /etc/grub.d/00_header ### 			 		
..............................
 I set the second timeout line to 0 to see if that changed anything and it still takes 37 seconds before it shows splash screen. any help please .

did you try the other suggestions?

---

### Post by jangozo on 2010-07-28
> **wallpaper_thief said:**
> did you try the other suggestions?

Has anyone tried the other suggestions and fixed it? I have and there are still no results.

---

