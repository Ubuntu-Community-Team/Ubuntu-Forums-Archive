---
title: "An Intriguing question about ubuntu on external hard drive.."
date: 2011-06-17
forum: General Help
---

### Post by bap.123prav on 2011-06-17
I was just thinking about installing an operating system like ubuntu or ubuntu server on an external harddrive. this being possible , i would like to know if we can use the external drive to plug into any machine and run my ubuntu by just changing the needed bios mods in that system. and without further having to install the necessary hardware specific devices into my os.
 
because each machine would have its own hardware set, how would the os handle it or would it have to install the necessary drivers and so on everytime it comes across a different system from the immediate previous hardware it was used with.
 
and i know this was why laptops were invented even maybe to have that portability to use with but this without a laptop, just an external hard drive that can make up and help us use the hardware at hand with ease without any installations of any kind.
 
just would like to know if it were even possible.

---

### Post by kanishkdudeja on 2011-06-17
even i want to be able to do that..:)

---

### Post by ajgreeny on 2011-06-17
It's certainly worth trying and in many cases will work with no problem as many drivers are in the kernel, not installed separately.

If proprietary drivers are needed for graphics card etc, then you might not be so lucky, but it is worth trying.

If you do decide to try this out you must remember to install the bootloader (grub) onto the external drive, or you will never get the system to boot to ubuntu, as there will be no grub files to run on your external's MBR.

---

### Post by oldfred on 2011-06-17
Info on installing:

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

The main issues may be video and wireless. If video may be able to do this, or just use generic drivers.

Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

If you have a wired connection initially, then it will download additional drivers on first boot or at least give you the option to download additional drivers.

---

### Post by bap.123prav on 2011-06-18
Thanks people. Ya basically the wireless and the graphics would be the main issue, in case of systems without an internet connection lets say i want to try it, would it still work with the basic generic drivers... ?

---

### Post by kanishkdudeja on 2011-06-18
thanks a lot..il try it out..:)

---

