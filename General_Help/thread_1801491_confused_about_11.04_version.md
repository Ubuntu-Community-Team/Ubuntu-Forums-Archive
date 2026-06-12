---
title: "confused about 11.04 version"
date: 2011-07-10
forum: General Help
---

### Post by AgentZ86 on 2011-07-10
[LIST]
[*]When you want to select a shutdown or reboot there is a selection for (reboot at complete update) what the heck does that mean and where the heck is the standard reboot feature ? 

[*]Additionally is the Nvidia drivers installed by default or not ? 
[*]I select additional drivers and it talks about some experimental driver that I can activate as opposed to the proprietary driver.

[*]Also in the Sytem/Preferences/Appearance there use to be options visual effects and you could select (none, normal, extra)

[*]Is 3D turned on by default for my nvidia driver or not ?
[/LIST]
I'm really a little confused about the changes in 11.04 version

Please advise
Thanks

---

### Post by coffeecat on 2011-07-10
> **AgentZ86 said:**
> When you want to select a shutdown or reboot there is a selection for (reboot at complete update) what the heck does that mean and where the heck is the standard reboot feature ? 

I don't follow what you mean by the first bit, but the restart option is in the list of you click on the shutdown button, top-right.

> **AgentZ86 said:**
> Additionally is the Nvidia drivers installed by default or not ? 

The proprietary nvidia driver is not installed by default, only the open source nouveau driver for nvidia cards.

> **AgentZ86 said:**
> I select additional drivers and it talks about some experimental driver that I can activate as opposed to the proprietary driver.

That is the package libgl1-mesa-dri-experimental which complements the nouveau driver for 3d. It works well enough for compiz with many nvidia cards. 

> **AgentZ86 said:**
> Also in the Sytem/Preferences/Appearance there use to be options visual effects and you could select (none, normal, extra)

If you want fine-grained control over compiz in Unity, install the package compizconfig-settings-manager.

> **AgentZ86 said:**
> Is 3D turned on by default for my nvidia driver or not ?

If you are getting the Unity desktop, then 3d is turned on. With nvidia cards you will get the classic gnome desktop as fallback until you activate either the proprietary driver or the experimental package. If you install the proprietary nvidia driver you need to know that there is a bug in Additional Drivers (Jockey) that causes it to tell you that the driver is installed but not activated. This is not so. If you are seeing the Unity desktop and you've installed the nvidia driver, it is activated. 

> **AgentZ86 said:**
> 
I'm really a little confused about the changes in 11.04 version


Then you might find the two links in my sig useful reading. :)

Good luck!

---

### Post by Frogs Hair on 2011-07-10
When you receive an restart to complete update message it is because you have installed an update that requires reboot to take be completed .

You will see this message after kernel and Xorg  updates . Restart is also required after driver installations .

---

### Post by AgentZ86 on 2011-07-10
> **Frogs Hair said:**
> When you receive an restart to complete update message it is because you have installed an update that requires reboot to take be completed .

You will see this message after kernel and Xorg  updates . Restart is also required after driver installations .

Ok, that makes sense thanks.

---

### Post by AgentZ86 on 2011-07-10
I don't think unity is install how can I tell ? 

When I installed, i did it from the usb pen drive and when it finished installing there was a message that Unity was not installed,but the system seem to be working fine.

However, I'm not convinced that any nvidia proprietary driver is installed.


I did not install any driver, and the only option seems to be to install the experimental driver.

I'm not use to seeing this since every system I ever used had an option to select the proprietary driver. This install does not.

The only selection available is the experimental.

Where do you get the proprietary driver that I once was so fond of seeing when you click additional drivers ?

All the other systems I have are still running 10.10 and working perfectly, but this system is a new install after the lighting storm and computer kill so I got this other system and figured I would install the latest version.

Thanks for all the responses.

---

### Post by Frogs Hair on 2011-07-10
If Unity is being used you will see the launcher panel on the left side of the screen like in my screen shot.

If you only have the experimental driver available you may not be able to run Unity 3D.

You can run Unity 2D by selecting it from session list below the greeter box on the login screen.

After you type your password before you login you will see the session list directly below the greeter box . It includes Classic Gnome , Ubuntu , Unity 2D , and other selections .

---

### Post by wildmanne39 on 2011-07-11
> **AgentZ86 said:**
> I don't think unity is install how can I tell ? 

When I installed, i did it from the usb pen drive and when it finished installing there was a message that Unity was not installed,but the system seem to be working fine.

However, I'm not convinced that any nvidia proprietary driver is installed.


I did not install any driver, and the only option seems to be to install the experimental driver.

I'm not use to seeing this since every system I ever used had an option to select the proprietary driver. This install does not.

The only selection available is the experimental.

Where do you get the proprietary driver that I once was so fond of seeing when you click additional drivers ?

All the other systems I have are still running 10.10 and working perfectly, but this system is a new install after the lighting storm and computer kill so I got this other system and figured I would install the latest version.

Thanks for all the responses.Hi, also run these commands in a terminal 
```
/usr/lib/nux/unity_support_test -p
```
```
lsmod
```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by AgentZ86 on 2011-07-11
> **Frogs Hair said:**
> If Unity is being used you will see the launcher panel on the left side of the screen like in my screen shot.

If you only have the experimental driver available you may not be able to run Unity 3D.

You can run Unity 2D by selecting it from session list below the greeter box on the login screen.

After you type your password before you login you will see the session list directly below the greeter box . It includes Classic Gnome , Ubuntu , Unity 2D , and other selections .

Darn it, i never see those screens because it logs in automatically on boot up

---

### Post by AgentZ86 on 2011-07-11
> **wildmanne39 said:**
> Hi, also run these commands in a terminal 
```
/usr/lib/nux/unity_support_test -p
```
```
lsmod
```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

> OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv18 20091015 
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no


> Module                  Size  Used by
nouveau               682322  3 
ttm                    76664  1 nouveau
drm_kms_helper         42136  1 nouveau
drm                   227495  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13400  1 nouveau
video                  19438  1 nouveau
vesafb                 13761  0 
snd_via82xx            29692  2 
binfmt_misc            17565  1 
gameport               19652  1 snd_via82xx
snd_ac97_codec        134270  1 snd_via82xx
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  2 snd_via82xx,snd_ac97_codec
ppdev                  17113  0 
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
snd_mpu401_uart        14169  1 snd_via82xx
snd_seq_midi           13324  0 
psmouse                73535  0 
edac_core              53845  0 
snd_rawmidi            30486  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36959  1 
snd                    67382  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
edac_mce_amd           23464  0 
shpchp                 37297  0 
i2c_viapro             13153  0 
k8temp                 13016  0 
soundcore              12680  1 snd
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
via_rhine              31816  0 
floppy                 74120  0 
pata_via               13632  2 


>  description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: KV2 Lite
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 01/29/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          slot: Socket 939
          size: 1800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl pni lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          slot: Socket 939
          size: 1800MHz
          capacity: 3GHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8
          resources: irq:0 memory:0-7ffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fb000000-fcffffff memory:e8000000-efffffff
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 4000]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: c1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:fb000000-fbffffff memory:e8000000-efffffff memory:fc000000-fc01ffff
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-disk
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.11
                serial: 5JXJKN8T
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b2664d99
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: ecbb38c4-c67b-394e-bd04-330da7339a36
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-07-04 07:24:47 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 17GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1021MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:fe00(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:fd00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:fc00(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:fb00(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fdfff000-fdfff0ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:f800(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:11:5b:c4:90:6d
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=xx.x.xx.xxx latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:f600(size=256) memory:fdffe000-fdffe0ff
     *-pci:1
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0


Thanks for the help

---

### Post by AgentZ86 on 2011-07-11
n18 driver is that experimental, default, or proprietary ? 

And does the pen drive install only install min. features or is it the same as thd CD install ? 

Thanks

---

### Post by AgentZ86 on 2011-07-11
crap, noticed something else too, it doesn't seem to like to reboot.

If will shut down and turn on, but when rebooting it never really shuts down and restarts. the computer stays running but the video never comes up and I don't think there is any indication that the system really is rebooting, I think it sort of suspends, and I have to hit reset to turn it on again.

Very strange first ubuntu I've seen any of this type of things it usually just works lol

---

### Post by AgentZ86 on 2011-07-11
Bahh, i get no options on the login screen nothing but login or select other for another user.

No other places to click anything at all.

---

### Post by wildmanne39 on 2011-07-11
> **AgentZ86 said:**
> n18 driver is that experimental, default, or proprietary ? 

And does the pen drive install only install min. features or is it the same as thd CD install ? 

ThanksHi, no you can install a complete system from the pen drive, if you downloaded the complete system. I have a laptop  like yours the only difference is I have 4 gigs of ram in it. 

It shows that unity is not supported, that could be because you do not have the right nvidia driver installed I am not sure, I have never used the nouveau driver. Your video card is older then mine that may make a difference. 

Also I noticed that you only have a few mega bytes of space for swap, you really need about 2 gigs with only one gig of ram and unity.

Did you upgrade or did you do a fresh install? 

Also you have to install unity 2D from synaptic or the software center to be able to use it. You should have other options at the log in screen. once you are booted since yours logs in automatically log out click on your user name go to the bottom of the screen click on ubuntu with no effects and see how that does. Then you can install unity 2d and you will be able to boot it by the same method I just described.

---

### Post by AgentZ86 on 2011-07-12
> **wildmanne39 said:**
> Hi, no you can install a complete system from the pen drive, if you downloaded the complete system. I have a laptop  like yours the only difference is I have 4 gigs of ram in it. 

It shows that unity is not supported, that could be because you do not have the right nvidia driver installed I am not sure, I have never used the nouveau driver. Your video card is older then mine that may make a difference. 

Also I noticed that you only have a few mega bytes of space for swap, you really need about 2 gigs with only one gig of ram and unity.

Did you upgrade or did you do a fresh install? 

Also you have to install unity 2D from synaptic or the software center to be able to use it. You should have other options at the log in screen. once you are booted since yours logs in automatically log out click on your user name go to the bottom of the screen click on ubuntu with no effects and see how that does. Then you can install unity 2d and you will be able to boot it by the same method I just described.


Thanks


Well, I changed the login from automatic so I could get the login screen this is how I knew there was no other options there.

From the settings of the login screen there is some options in the pulldown to give me a selection but unity is not one of them.

So I suspect it's related to the video card. So I do have another card I could try and see if that does it. But I'm wondering if those feature will just appear or an upgrade made cause it to install or would I have to install from fresh again.

This is a new fresh install on a desktop not laptop, and I installed from flash drive so it should be a complete install from what your saying same as the CD version ? 

Anyhow thanks for the help so I either need to get driver support or a new vid card from what your telling me.

I'll play with it some more thanks

---

### Post by AgentZ86 on 2011-07-12
Oh one last thing, when I click on additional driver, and there is NO option for nvidia driver. The only option showing is to install the experimental driver.

But if the experimental driver is already installed then why would I do it again. This does not sound right I don't think I should really install it or activate it so I'll leave it alone for now until I can figure out how to get the driver or another vid card installed.

Thanks

---

### Post by mastablasta on 2011-07-12
> **AgentZ86 said:**
>  
Well, I changed the login from automatic so I could get the login screen this is how I knew there was no other options there.
 
 
you need to click on the user as if you plan to login first. 
 
> 
This is a new fresh install on a desktop not laptop, and I installed from flash drive so it should be a complete install from what your saying same as the CD version ? 

 
yes, it's the same iso image, so it's also a same install.

---

### Post by AgentZ86 on 2011-07-12
Ok so I see on the login screen at the bottom very small the session options which is the same as the options shown in the System/Administration/Login Screen

But Those options are as follows
Ubuntu
Ubuntu Classic
Ubuntu (no effects)
Ubuntu safe mode
Recover Console

Nothing about any unity, but let me ask does the new 11.04 install with unity by default if the video card supports it, or is this something that people select ?

So now I guess I have to install the proprietary driver for this unless it's not supported any more

---

### Post by wildmanne39 on 2011-07-12
Hi, the one that says ubuntu is unity, it does not say unity, just see if you can log into ubuntu.

---

### Post by AgentZ86 on 2011-07-12
> **wildmanne39 said:**
> Hi, the one that says ubuntu is unity, it does not say unity, just see if you can log into ubuntu.

ahhh, ok thanks


I now need to install the 96 version of nvidia driver.

But synaptic won't install it and it appears there is issues with the MX 4000 nvidia card.

I've been all over google trying to figure this out and so I think I'm sort of stuck at this point unless I can install the driver.

The thing is the system is working, but just a few things missing and it appears video related.

On ebay when you want to add pictures and you see the browse to screen and normally you would see the gnome and file, but the screen is all white with some text, and the window widgets appear to be sort of inactive even though they are working but you can't really tell if you get any button pushes or anything because there is no buttons to click ok etc. it's just black text over white screen.

I suspect video driver. Because mostly everything else appears to be working correctly except some video aspect now.

Thanks for the help

---

### Post by wildmanne39 on 2011-07-12
Hi, is the experimental driver the only other driver in there for your card? If so I guess you can try it, also it is possible that support for your card has been discontinued since it is an older card, but I am not sure about that.

---

### Post by AgentZ86 on 2011-07-19
Ok, i've noticed also some other changes that seem very inconvenient as well.

For (start up applications) on 10.10 there use to be an options tab that you could select to start currently running applications.

This tab is no longer included in the 11.04. So now what ? 

How do I include the currently running applications as I did once before.

It was so easy and convenient before.

:confused:

---

### Post by AgentZ86 on 2011-07-19
My problem may not be related to the currently installed driver either.

When I open any browser based feature that asks to browse to a location of a file the screens are white with black text backround.
When in this type of feature the gnome navigation at the top that shows the file structure
Just black text on white back for the folder hierarchy. Seems to still work but something is really missing.

When you select a file or files with ctrl+a to select files they are not highlighted so you don't know if your really selecting the correct file.

I had assumed this was because some of my 3d stuff was not available for my vid card since the nvidia 96 drivers don't work without some configuring , but now I'm not so sure this is a video problem

I installed the java6 mozilla plugins with synaptic since the java addons and plugins in firfox do not appear to be installed by default.

The java plugin did not effect anything and I still get white back with black text for any browser feature that asks to browse to a file location. Seem that something is mission either in the browser,plugin or graphics ? 

I'm leaning toward the plugins topic now but really not sure.

Example:
Yahoo email/compose mail/attachments/browse  black text on white backround and no buttons,borders of buttons or colors.

No highlighting of selected files etc. just black and white.

Strange

Please advise


Please advise
Thanks

---

