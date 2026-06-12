---
title: "Gnome startes instead of Unity"
date: 2011-05-01
forum: General Help
---

### Post by Jonker on 2011-05-01
Hello,

I have Ubuntu 11.04 installed on a desktopcomputer (nVidia GeForce3 Ti 200). My Unity version is 3.8.10. 

When I first installed Ubuntu 11.04, it always gave me the message "It seems, that you dont have the Hardware required to run unity". So I updated the driver (or actually installed it from additional drivers). The message didn't pop up again. But when I boot, and log in to and Ubuntu session, still Gnome 2.32.1 starts (which is the classic mode). 
So I think, that i would need to restart Unity.

I did so, with the command ```
compiz --replace
```But it gave me an errormessage:
```
compiz (unityshell) - Error: OpenGL 1.4+ not supported
compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Could not activate plugin 'unityshell'
```Any suggestions, what to do?

Thanks for your help

Jonker

---

### Post by Jonker on 2011-05-05
Or dose the pc just not meet the hardware requirements? Driver issue?

My System:
Intel Pemtium 4 @ 2Ghz
nVidia GeForce 3 Ti 200

or is it a xorg.conf issue?

Thanks for your replies....

Jonker

---

### Post by coldraven on 2011-05-05
I think it is a bug.
11.04 installed and ran fine for a week with Unity as default.
Then without me doing anything after boot-up I got the same error message as you did and it booted into "Gnome Classic".
The next day, after an update it fixed itself so I have no idea what went wrong.

---

### Post by Nerotriple6 on 2011-05-05
I may be wrong but it appears that your card lacks good enough Open-gl support. As your command output suggests..
It is a very old card.. :(
So yes I'm guessing it doesn't meet the requirements.

Do you know about the card? It was hard finding much information about it. How much memory it has? How far Open-gl support goes?

---

### Post by Jonker on 2011-05-05
> It is a very old card..
Yes, thats true... , but couldn't the processor take some of the jobs from the graphing card?

PS: Win XP Prof. is working absolutly fine, and Gnome 3 did the same (I had used it, but did a fresh install, so this wont mess it up)

> Do you know about the card? It was hard finding much information about it. How much memory it has? How far Open-gl support goes?

No, not much... Can you give me commands, to find out more informations?

Thanks

Jonker

---

### Post by Jonker on 2011-05-05
I input the ```
lshw
``` and got this:
```
  [FONT=&quot]buntu-laptop-pc
    description: Computer
    [/FONT][FONT=&quot]width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=hardware-failure-fw cpus=1 power-on_password=enabled uuid=44454C4C-3700-104B-8058-B6C04F42304A
  *-core
       description: Motherboard
       product: Dimension 8200
       vendor: Winbond Electronics
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A08
          date: 08/30/2002
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     [/FONT][FONT=&quot]*-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.90GHz
          [/FONT][FONT=&quot]vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.1.2
          slot: Microprocessor
          size: 1900MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          [/FONT][FONT=&quot]configuration: id=0
        *-cache:0
             description: L1 cache
             [/FONT][FONT=&quot]physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        [/FONT][FONT=&quot]*-cache:1
             description: L2 cache
             physical id: 701
             [/FONT][FONT=&quot]size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
             physical id: 0
             slot: RIMM1
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
             physical id: 1
             slot: RIMM2
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns) [empty]
             physical id: 2
             slot: RIMM3
             clock: 400MHz (2.5ns)
        *-bank:3
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: RIMM4
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82850 850 (Tehama) Chipset Host Bridge (MCH)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82850 850 (Tehama) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fc000000-fdffffff memory:f0000000-f7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV20 [GeForce3 Ti 200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fc000000-fcffffff memory:f4000000-f7ffffff memory:f3f80000-f3ffffff memory:f0000000-f000ffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fe100000-fe2fffff
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:ece0(size=32)
[/FONT]
  
```
This is only the first part...

So by the looks of it, the intressting part is:```
  [FONT=&quot]*-display UNCLAIMED
                description: VGA compatible controller
                product: NV20 [GeForce3 Ti 200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fc000000-fcffffff memory:f4000000-f7ffffff memory:f3f80000-f3ffffff memory:f0000000-f000ffff
[/FONT]
  
```

Jonker

---

### Post by Jonker on 2011-05-06
Ok, I think, Ill just leave Unity. 

Do you know and good Windows Maganager? Gnome3, KDE?

thx

---

### Post by Nerotriple6 on 2011-05-06
I know there is a command for ATI cards to display temperature but that's all I know, sorry.
I like Gnome and Gnome 2 is what I use. When you log in, click on your username and look at the panel at the bottom.
Where it says "Ubuntu" there is a menu, try selecting "Ubuntu Classic". What happens when you have entered your password and logged in?

---

