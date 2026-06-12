---
title: "Error 18: selected cylinder exceeds maximum supported by bios"
date: 2010-03-16
forum: General Help
---

### Post by zakoo2 on 2010-03-16
Hi!
I have an MSI U100 Plus netbook with a shared 160GB SATA HDD with Windows 7 and Ubuntu 9.04 on it. Windows 30GB, Ubuntu 40GB, and an additional NTFS partition with 90GB. I had a problem with windows, had to reboot, and than I chose "run windows normally". It didn't load, so I had to reboot once again, than I got this message:
"Error 18: selected cylinder exceeds maximum supported by bios"
I tried to boot from an Ubuntu Live CD, I got a bunch of error messages, but after a while I could use the system. I reinstalled GRUB (found this tutorial, which already worked for me once: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351))
I rebooted, and got this error message:
"Boot Failure
Press any key to continue"
Plz help, I have absolutely no idea what to do!!!
P.s.: I'm from Hungary, so sorry for the mistakes!

---

### Post by sandyd on 2010-03-16
> **zakoo2 said:**
> Hi!
I have an MSI U100 Plus netbook with a shared 160GB SATA HDD with Windows 7 and Ubuntu 9.04 on it. Windows 30GB, Ubuntu 40GB, and an additional NTFS partition with 90GB. I had a problem with windows, had to reboot, and than I chose "run windows normally". It didn't load, so I had to reboot once again, than I got this message:
"Error 18: selected cylinder exceeds maximum supported by bios"
I tried to boot from an Ubuntu Live CD, I got a bunch of error messages, but after a while I could use the system. I reinstalled GRUB (found this tutorial, which already worked for me once: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351))
I rebooted, and got this error message:
"Boot Failure
Press any key to continue"
Plz help, I have absolutely no idea what to do!!!
P.s.: I'm from Hungary, so sorry for the mistakes!

means you have a corrupted partition table or a damaged hard disk.
Delete (wipe) everything on the drive, then try installing ubuntu again.

---

### Post by zakoo2 on 2010-03-16
Is there any chance I can save the NTFS (Windows) partitions, and only reinstall Ubuntu, so that I don't have to install Windows again?

---

### Post by Mark Phelps on 2010-03-16
> **zakoo2 said:**
> Is there any chance I can save the NTFS (Windows) partitions, and only reinstall Ubuntu, so that I don't have to install Windows again?

I'm presuming you do NOT have a Win7 Installation DVD, right?

Given that you were going to mess with partitioning, you should have used the new builtin backup feature in Win7 to create and burn a Win7 Repair CD.

IF you go to the NeoSmart Technology forums, you will be able to download a Win7 Repair CD image that you can then burn to a CD to make a Repair CD.

Once you have that, boot into the  Repair CD and run Startup Repair three times.  That should get you booting into Win7 again.

---

### Post by dcstar on 2010-03-17
> **zakoo2 said:**
> 
.......
I tried to boot from an Ubuntu Live CD, I got a bunch of error messages, but after a while I could use the system. I reinstalled GRUB (found this tutorial, which already worked for me once: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351))
.......

Which Grub did you "reinstall", grub-pc (grub2) or grub-legacy?

Also you may want to check the hard disk settings in the BIOS.

---

