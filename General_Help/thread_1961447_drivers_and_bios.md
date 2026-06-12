---
title: "drivers and bios"
date: 2012-04-19
forum: General Help
---

### Post by jpg123 on 2012-04-19
Sorry to ask another obvious question, but how do i update my drivers and bios in ubuntu?

---

### Post by josephmills on 2012-04-19
Welcome to Ubuntu Forums.
we love questions Here :) 
there are plenty of ways to update your "Drivers" we call them moduals in nix See in gnu/linux everything well almost every thing is open-source this means that you do not have to go to some site to get driver because we have already made free and or open-source ones there are the cases that the company that sux will not release the source code or put crazy laws on there software. that is where additional driver aka jocky-gtk comes into play. Or you can got to the site and go grab there stuff and compile. but you do not have to do that anymore as there are so many open-source modules. Also the good thing about open-source is when ever a software developer makes a change to the software ie updates makes better. You also get that update :) oh yeah and for free .You can see all of them modules that are installed by opening your terminal ctrl+alt+t and enter in ```
lsmod
```now you can update them with the command 
```
sudo apt-get update && sudo apt-get upgrade
```as far as your bios goes this is a tricky one what is computer model and make ?

---

### Post by anejo on 2012-04-19
Drivers: if your 'Additional Drivers'--in System Settings--is up to date or not showing any updates + the system is regularly updated... then you're good to go.

BIOS: you need to go the OEM website of your make and model and find a BIOS update. The hardware manufacturers are pretty good with releasing those images. You can burn a CD and flash the BIOS accordingly!

---

### Post by codemaniac on 2012-04-19
Hello Mate ,
You need to determine the vendor of your Hardware.Did you purchase this computer as a bundled, pre-built system, or was it assembled from purchased components? 
The larger, more popular manufacturers and builders include companies such as Dell/Alienware, HP/Compaq, IBM, Lenovo, Sun, Gateway,Acer, etc. For these, visit the manufacturer's site. For a custom system built from purchased components, visit the motherboard manufacturer's website.

---

### Post by codemaniac on 2012-04-19
```
sudo dmidecode --type bios
```
can give you good amount of information about you bios .

---

### Post by jpg123 on 2012-04-19
this i what i get for that code -
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.41
    Release Date: 10/11/2011
    Address: 0xE0000
    Runtime Size: 128 kB
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
    BIOS Revision: 15.65
    Firmware Revision: 9.71

another problem that ive got is that i think ive installed a 32 bit version of ubuntu instead of a 64 bit, would i have to reinstall or can i make an upgrade to the 64bit when i install 12.04 next week. My drive.rs seem to be up to date in the additional drivers app so that seems to be ok.

---

### Post by grahammechanical on 2012-04-19
My motherboard came with a maker's CD that had various Windows drivers and Utilities. One of these utilities would allow me to update my BIOS from inside the Windows operating system, if I had it. Which I do not.

I cannot update my BIOS from inside Ubuntu because the motherboard maker did not supply a Linux utility for doing that.

It is the motherboard maker's responsibility to provide the means to update the machine's BIOS. Original Equipment Makers (OEM) just do not see any commercial reason for giving Linux utilities/drivers with their equipment.

This failure on the part of the manufacturers is the reason that Linux comes with drivers as standard. They are loaded as modules when we boot. Linux developers have to craft these drivers. This is why Linux does not always support the very latest hardware. It takes time for these dedicated developers to workout how the latest hardware works so that they can produce a driver.

If you run Update Manager regularly then drivers will be up dated as and when an updated driver is available.

Please remember, Linux is not a different/cheaper Windows. It is much more than that!

Regards.

---

### Post by Mark Phelps on 2012-04-19
Hey ... it's your PC, so it's your choice ... but you really should NOT be messing with your BIOS unless you have a particular problem which you know is fixed in a BIOS update.  Unless you have one of the newer motherboards which have Dual BIOS, if anything goes wrong during the BIOS update, your PC will suddenly become an "electric brick"!

That said, if you really want to do this, you need to check the motherboard manufacturer's website to see what they offer for BIOS upgrades.  They all offer something ... but it's typically a Windows app that you have to run.

However, some motherboards offer the capability to do a BIOS upgrade by pressing a special key combination on startup and sticking in a diskette (for older boards) or a USB stick (for newer boards).

Once again, you need to check your motherboard manufacturer website to see if they have documentation on this.

---

### Post by jpg123 on 2012-04-19
yeah i dont think i have enough knowledge yet to mess about with the bios, so ill leave that. Thanks for the advice though.

---

### Post by codemaniac on 2012-04-19
Rightly advised by Mark Phelps , you should not mess up with your bios unless there is something making your life hell .If you are having any specific problem in your bios , please post here , people can suggest other way out than simply upgrading/reinstalling the sw .

---

