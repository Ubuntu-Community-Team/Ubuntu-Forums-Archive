---
title: "MCP79 SMBus Error on Boot"
date: 2010-05-15
forum: General Help
---

### Post by Jose Catre-Vandis on 2010-05-15
Since installing Xubuntu 10.04 I get an error after grub but before the splash screen:

```
[   16.215435] nForce2_smbus 0000:00:03.2: Error probing SMB2.
```

If I run dmesg after boot up I get a bit more info:

```
[   16.215418] ACPI: resource nForce2_smbus [0x2e00-0x2e3f] conflicts with ACPI region SM00 [0x2e00-0x2e3f]
[   16.215435] nForce2_smbus 0000:00:03.2: Error probing SMB2.
```

If I run sudo lshw I see

```
*-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:2f00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:15 ioport:2900(size=64) ioport:2d00(size=64) ioport:2e00(size=64)
```

In trying to run lm-sensors my smbus is not recognised, therefore i can read temperatures etc.

This is on an Asus EB 1012 nettop Atom 1.6 with ion graphics. Can anyone advise how to fix?

---

### Post by Jose Catre-Vandis on 2010-05-16
Seems that by adding
```
acpi_enforce_resources=lax
```
to the boot line makes the message go away :)

The quick way to do this is to edit **/boot/grub/grub.cfg** and append to the boot line, but this will get wiped out if you update grub.

The "better" way is to edit **/etc/default/grub** and add the entry to the **GRUB_CMDLINE_LINUX_DEFAULT=** line

Mine looks like this now:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax quiet splash"
```

Don't forget to 
```
sudo update-grub
```
if you use the "better" way

This only seemed to affect my main distro from where grub is running, not other distros?

BTW I re-ran sensors-detect and found that things were better, and running coretemp provided me with temperature info for CPUs and MB.

---

### Post by SchneiderIS on 2010-07-04
Thank you for this excellent post.  Clear, accurate, and exactly what I needed.

---

### Post by ghelbere on 2010-07-20
Great. I searched several days for this solution.
Thanks for sharing the fix with us !

---

### Post by Zipstor on 2010-08-16
Dear Jose,

I wish to attract your attention on my thread. It involves the same error but have a nasty bug that does not allow me to go ahead with your instructions.

[http://ubuntuforums.org/showthread.php?t=1523191](http://ubuntuforums.org/showthread.php?t=1523191)

I've had some help from EFnet, Freenode etc... But no success.

Please feel free to let us know if you have a good idea that could help.

z:/

---

### Post by Jose Catre-Vandis on 2010-08-17
> **Zipstor said:**
> Dear Jose,

I wish to attract your attention on my thread. It involves the same error but have a nasty bug that does not allow me to go ahead with your instructions.

[http://ubuntuforums.org/showthread.php?t=1523191](http://ubuntuforums.org/showthread.php?t=1523191)

I've had some help from EFnet, Freenode etc... But no success.

Please feel free to let us know if you have a good idea that could help.

z:/

You can add "acpi_enforce_resources=lax" to your command line if you enter the grub menu on boot up and do the press "e" thing, perhaps doing it that way will get you to the desktop.

Having read your other thread (what problems :(), why not try the Alternate CD to install, as this uses a non X interface.

---

