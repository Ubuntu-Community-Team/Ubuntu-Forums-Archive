---
title: "system hangs after new instalation"
date: 2012-10-13
forum: General Help
---

### Post by rnerwein on 2012-10-13
hello

after installing 
             DISTRIB_ID=Ubuntu
#           DISTRIB_RELEASE=4.10
#           DISTRIB_CODENAME=precise
#           DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

on my:

tschang
    description: Desktop Computer
    product: Aspire X3200
    vendor: Acer
    version: R01-A3
    serial: 983ORE5DAP83904F133003
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop power-on_password=disabled
  *-core
       description: Motherboard
       physical id: 0
       version: JM800QLU-2G
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: R01-A3 (07/31/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd
          int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen
          int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
          biosbootspecification

--> when i select the new installation the system hangs forever with a black
            screen. i turn of my pc and after reboot i select "edit" in the grub menue
            and change the startup to single user and rw.
        on the console screen now i can see the folowing messages:

                        nouveau 0000:02:00 invalid ROM contents
                       nouveau 0000:02:00 no valid BIOS image found
                       nouveau 0000:02:00 Register 0x00004030 not found in PLL

when i remove the xorg.conf --> same result.
but some times the system show me the UBUNTU screen with the moving
dots - but even for ever.

====> ( windows, suse, solaris10 and ubuntu lucid are running fine on this pc.)

VGA is:
*-display
             description: VGA compatible controller
             product: C77 [GeForce 8200
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list rom
             configuration: driver=nvidia latency=0^M
             resources: irq:20 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable)
*-display^
             description: VGA compatible controller
             product: G98 [GeForce 9300 GE]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:16 memory:f8000000-f8ffffff memory:c0000000-cfffffff(prefetchable)
                              memory:f6000000-f7ffffff ioport:ac00(size=128)
                              memory:f9000000-f901ffff(prefetchable)



help - any idea

---

### Post by Bashing-om on 2012-10-13
rnerwein;  Hi !

I would have expected "single user mode" to boot up.....

Uhmmm..how bout seeing if you can boot up with the "nomodeset" option in the grub command line of the booting kernel ?

Then, once booted in, with the additional drivers utility see if a proprietary driver can be installed ? nouveau = open source
[INDENT]hth <==BDQ

[/INDENT]

---

