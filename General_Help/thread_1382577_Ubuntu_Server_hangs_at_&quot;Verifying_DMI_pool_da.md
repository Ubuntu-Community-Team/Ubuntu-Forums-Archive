---
title: "Ubuntu Server hangs at &quot;Verifying DMI pool data&quot;"
date: 2010-01-16
forum: General Help
---

### Post by FCarlo on 2010-01-16
[B]Hi!
I've got a problem with a Server that I have built! It has got two 1TB SATA Hard-drives for my Data and one old 20GB IDE Hard-drive for the OS (Ubuntu Server 8.04). The installation worked fine but then the Computer hanged "Verifying DMI Pool Data"! When I de-connect the IDE Hard-drive it starts Grub, but of course spits out Error 21! I know there are millions of posts on this, but they al say the folowing and don't solve the Problem:[/B]

[I]Q. During bootup my computer hangs at "Verifying DMI pool data." What is it and how do I fix it?

A. DMI or DesktopManagement Interface (pdf) is a layer of abstraction between system components and the software that manages them. The System Management BIOS (SMBIOS) is an extension of the Basic Input Output System (BIOS) that formulates and delivers this information to the operating system. The pool data is the information. In short, when the BIOS is "Verifying DMI pool data" it is verifying the table of data it sends to the operating system (Windows, etc.). If it isn't sucessful, it should return an error. Wait a reasonable period of time for it to finish. It may make take some time or it may be stuck. Possible fixes:

1. If you changed the hardware just before this problem occurred (e.g., installed a new hard disk drive), unchange it.

2. If you installed a new hard disk drive, set the motherboard CMOS Setup to Auto for the drive type. You may have to disconnect the drive first.

3. Enable "Reset Configuration Data" (may be "Force Update ESCD" in some CMOS Setuups) in the motherboard CMOS Setup PNP/PCI configuration. (Rebooting will automatically disabled it after it has done its thing.)

4. The CMOS may be corrupted. Clear it.

5. Disconnect all drives not required to boot the computer. If this fixes it, reconnect one at time.

6. The floppy drive may be bad or not connected properly.

7. Reseat all expansion boards.

8. Pull all boards not required to boot the computer.[/I]


**So if some one can help me please Reply!!!**

---

### Post by bsh on 2010-01-16
- this has nothing to do with ubuntu server, it's a hardware/bios problem
- how does grub start, if you have disconnected the system drive? did you install grub onto another drive(s)?? (obviously yes)
- check the jumper settings on the ide drive. do not use cable select. set it to master and connect it to the END of the ide cable. some drives (western digital) have different settings for "master with slave" and "single master". if the drive is alone on the ide cable, set it to "single master". if there is a slave drive too on the same cable, set it to "master with slave"
- if there's another drive on the same cable, set it to be slave via jumper settings.
- replace the ide cable. they break easily and may cause funny errors like this.
- make sure in bios, that the boot device order is allright, and that it boots from the ide drive.
- "Enable "Reset Configuration Data" (may be "Force Update ESCD" in some CMOS Setuups) in the motherboard CMOS Setup PNP/PCI configuration."
- remove all other drives and reinstall grub mbr onto the ide one, and only that one.

---

### Post by FCarlo on 2010-01-16
My Motherboard is a ABIT AW8D! Were is "Reset Configuration Data"??? And grub is installed on the IDE Driv! Help!!!!!

---

