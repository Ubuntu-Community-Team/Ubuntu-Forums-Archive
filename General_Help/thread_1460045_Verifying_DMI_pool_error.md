---
title: "Verifying DMI pool error"
date: 2010-04-22
forum: General Help
---

### Post by Foredeck on 2010-04-22
I recently started having problems when I boot my computer.  It hands at "Verifying DMI pool error"

I had windows Vista installed and I formatted it about 6 months ago, and installed ubuntu on the machine.  I ran it without problem untill about a week ago when I started having these problems

I did not change any hardware in the machine, or even open the computer at all.  

Last night, the computer froze while the hard drive was working hard.  I was copying quite a bit of files, and downloading a few documents.  So, the hard drive may be stressed.  

Is it possible that some corruption in the hard drive would cause this?  And, how would I test it?

I don't think I've lost data on the hard drive.  I haven't checked every file, but I haven't had any corrupted files.

---

### Post by klemes on 2010-04-22
It seems a computer BIOS related error.
During initial boot try to enter the BIOS settings screen (by pressing ESC or F1 or whatever instruction it gives you at the initial boot screen in order to access BIOS setup) and search for a Load default settings or Load Optimal settings option.Choose this and answer yes as confirmation.That may or may not help alleviate the error but one cannot be sure.
An other solution would be to flash your BIOS if you are familiar with the procedure.
Note there is also a command line tool called dmidecode (used with sudo as root) that you could use to verify the contents of your DMI registers and look for something peculiar for example.

---

### Post by P4man on 2010-04-22
Agreed with the above poster. Most likely your bios configuration data got corrupted. Restoring bios to its defaults might help, if not, try flashing the bios.

---

### Post by Foredeck on 2010-04-22
I restored the bios, but no luck, got the same results. 
 
What is the best way to flash the bios?  I've been reading a bit, and the flashrom seems the simplest way. 
 
>  
Read this HOWTO and wonder what's it all about? Why wouldn't you just use FLASHROM [http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

install with 

> sudo apt-get install flashrom.

Backup your existing bios with 

> sudo flashrom -r original.rom

Write the new one with

> sudo flashrom -w new.rom

reboot and be happy.


---

### Post by P4man on 2010-04-22
Thats for coreboot, an opensource attempt to replace the bios, but almost certainly not  for your bios!

To upgrade the bios, check with your motherboard vendor and hope it gives you bootable cd or usb option, and not just a windows only solution (or floppy only, unless you still have a floppy).

edit: oops, maybe im wrong about the coreboot utility. If that actually works, that would be awesome.. let me look in to it a bit more.

edit bis: indeed. It does exactly that. Im impressed! So yeah, if your bios chip is supported (which seems highly likely), all you have to is download the bios rom file from your motherboard vendor (make VERY VERY sure you get the right one for your exact motherboard) and use those instructions to flash it.

That said, I thought bios corruption  typically  happened in the user settings, so overwriting the bios itself may not achieve anything. Still worth a try though.

---

