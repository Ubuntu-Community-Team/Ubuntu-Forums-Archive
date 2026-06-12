---
title: "No Installable kernel was found in the defined APT source"
date: 2010-08-11
forum: General Help
---

### Post by cj13579 on 2010-08-11
Hi all,

I am trying to install ubuntu on an old machine and no matter what version I try to install I get this same error. 

"No installable Kernel was found in the defined APT sources"

The versions I have tried are (9.04server. 9.10desktop, 10.04 server).

I have swapped both the CD drive and HDD drive becuase, well i don't know why, but I have. This didn't work.

I have read ([http://ubuntuforums.org/showthread.php?t=3444](http://ubuntuforums.org/showthread.php?t=3444)) and have tried changing my BIOS settings so that i have my config is:

IDE Primary Master : Maxtor 6Y080L0 (HDD)
IDE Primary Slave  : HL-dt-st-sl8480b (CD-DRIVE)

This didn't work.

I have also tried doing the instructions posted by migraineman on the second page of the thread mentioned above but this also didn't work.

My specs are:
Cyrix 6x86 Processor
80Gb Maxtor HDD
LG-GCE CD-ROM Drive
319Mb RAM - 8Mb Shared


Thanks in advance,

Chris

---

### Post by Fludizz on 2010-08-11
Wow! That's really old hardware... As far as I can read, you should try  Ubuntu 8.04 LTS, that version uses the 2.6.24 kernel and in the kernel  bug tracker it is noted as working for the 6x86 CPU.

Keep in mind, though, on such old hardware you'd rather have a very  lightweight distro...

---

### Post by cj13579 on 2010-08-11
Ha, thanks for the reply. 

So I think it was a compatability issue with the motherboard. From what I was able make out the installer comes up with that message when it tries to install all the Kernels that it has (on the CD I presume) and if it none of them load it kicks out that message.

Put it on a machine that is a little bit more recent and BINGO, all fine. Typical!

---

### Post by kandresen on 2010-10-17
I am having the same "No Installable kernel was found in the defined APT source" error message on brand new hardware (Asus UL30VT as well as a newer Acer laptop) when trying to install of Ubuntu 10.10 amd64 from USB stick. This happen with both 10.10 amd64 alternative image and desktop image. I have verified the checksums (a8d8e24bf8b82b4302d074fcac380d65 for alternative and 1b9df87e588451d2ca4643a036020410 for desktop version). 

For the Desktop version I have attempted using with and without adding the "update"- and the "3rd party" repositories during install with the same results. 

I am noticing that there was a bug #291670 with Intrepid that may be similar to this problem(?) I have tried to make the image on two machines, one upgraded to Ubuntu 10.10 amd64 from 10.04 with all the updates, the other from a 10.04 amd64 install kernel from 10.10. 

Notice that I have also tried installing 10.04 from a USB stick created with the same Startup Disk Creator. I am getting an error message during install with the 10.04 amd64 image too, though one that is more like a warning and finish with a successful install. 

Are someone else experiencing problems using? Could this be related with the usb creation scripts(?) I did drop to a shell and attempted to do the "alt-f3", "chroot /target" and "apt-get install kernel-package" suggested from another post from another post about similar problems with ubuntu 9.10, however the "kernel-package" could not be found.

Any suggestions?

---

### Post by nickbooker on 2010-10-19
I had this problem with a Viglen MPC-L.

The solution I found was to let the installation continue (say Yes to the message asking if you want to continue without installing a kernel).

Then, when the final prompt "Installation complete" appears (i.e. the one that appears just before it goes down for reboot), do the following:
[LIST=1]
[*]Press Alt+F3 to switch to a virtual console, then press Enter to activate it.
[*]Type "apt-install linux-image-generic"
[*]Wait for the prompt to re-appear (you can monitor progress by pressing Alt+F4, but you must Alt+F3 to see whether it's actually finished)
[*]When the installation of the kernel is complete, press Alt+F1 to return to the installer, and press Enter with the Continue button highlighted to reboot the system
[/LIST]

Then all you need to do is cross your fingers that the kernel installed is suitable for your machine.

---

