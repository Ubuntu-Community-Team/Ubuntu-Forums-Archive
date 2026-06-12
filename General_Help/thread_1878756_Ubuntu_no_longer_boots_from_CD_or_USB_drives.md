---
title: "Ubuntu no longer boots from CD or USB drives"
date: 2011-11-10
forum: General Help
---

### Post by Rebelli0us on 2011-11-10
I installed Ubuntu on a friend’s new machine a few months ago. OS boots from hard disk and works just fine, **but** the machine will no longer boot Ubuntu Desktop from CD or USB flash drive.

Windows CD boots fine.
DOS boots OK from USB (I did a BIOS update).
I also burned ISO on the machine itself in case the DVD drive is fussy.
I tried BIOS set to SATA instead of AHCI
I tried OpenSUSE, no boot
I tried booting gparted-live CD, no boot
Memtest OK

In all cases the Linux kernel loads fine, then OS fades to black, no errors on screen. . .

CD booting obviously worked OK because that’s how I installed Ubuntu!
USB booting worked OK too, my friend booted Ubuntu for a while.

I’m stumped on this one, especially since WinXP cd boots ok. Any ideas?

---

### Post by Mark Phelps on 2011-11-10
If you've confirmed that these same other CDs boot fine in another PC, then my only guess at this point is that the lens in this CD/DVD drive needs to be cleaned.  You can buy cleaners for $10 USD or so.

As to why the same drive would read MS CDs but not other CDs, really have no idea -- especially if the same CDs boot OK in another PC.

---

### Post by WasMeHere on 2011-11-10
Hi Rebelli0us,

Did I understand correctly, that you changed the BIOS? Maybe that is causing the problem.

It might be that you have to change some setting in the first menu of the Ubuntu live system (if you get there). So during boot, when you see a small symbol press Enter! Otherwise it skips the menu and continues with a default setting, that may not work now on your friend's computer. *Edit: This may vary between the versions (10.04 LTS works as described, I am not sure what it looks like in 11.10).*

If you get a menu, it should be possible to understand. In 10.04 you use the F6 key to get to a submenu.

Good luck :-)
Olle

---

### Post by Rebelli0us on 2011-11-10
> **Olle Wiklund said:**
> Hi Rebelli0us,

Did I understand correctly, that you changed the BIOS? Maybe that is causing the problem.

It might be that you have to change some setting in the first menu of the Ubuntu live system (if you get there). So during boot, when you see a small symbol press Enter! Otherwise it skips the menu and continues with a default setting, that may not work now on your friend's computer. *Edit: This is depending on the version (10.04 LTS works as described, I am not sure what it looks like in 11.10).*

If you get a menu, it should be possible to understand. I think you should use one the Function keys (I don't remember, maybe F4 or F6) to get to a submenu.

Good luck :-)
Olle


Thanks Olle. I too thought it might be a bug in the newer BIOS, so I temporarily switched to the original BIOS, but the problem is still there. I also cleared NVRam in cmos.

I do get to the Linux menu, and as I said above the kernel loads fine but something goes wrong after that. Gparted live CD fills the screen with debug info, it goes well past preseed stage, but it goes black too.

Some mobos are linux unfriendly, but this one booted before so I’m really stumped. I need to boot the Desktop CD to do a repair and I can’t. It’s a very special machine, I’ll try post some pics soon.

---

### Post by WasMeHere on 2011-11-10
If you have important repair work to do, I suggest that you try either Ubuntu 10.04 LTS or 8.04 LTS (yes, it is old, but it is good at starting) or Knoppix (it is also good at starting because it is good at recognizing hardware). The Knoppix CD has several repair tools.

*Edit: browse the internet to find out about the so called cheat-codes of Knoppix (= start-up options).*

---

### Post by Rebelli0us on 2011-11-11
Somebody else having the same problem, very advanced:

[Can't boot live cd or usb on machine with radeon 6870]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/463067-cant-boot-live-kde-cd-usb-machine-radeon-6870-a.html") 

The short story, in desktop CD I used startup option "nomodeset" and it booted

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206965&stc=1&d=1321041511[/IMG]

USB boot fails with an error message the repeats forever. What does that mean?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206966&stc=1&d=1321041511[/IMG]

I don't remember using any startup options when I first installed on HD so I'm still puzzled.

---

### Post by WasMeHere on 2011-11-12
The word 'gfxboot' indicates that it is about graphics, actually graphics during boot. Browse the internet for detailed information!

Can you make the USB boot get to the screen where you can select boot options?

---

### Post by Rebelli0us on 2011-11-12
> **Olle Wiklund said:**
> The word 'gfxboot' indicates that it is about graphics, actually graphics during boot. Browse the internet for detailed information!

Can you make the USB boot get to the screen where you can select boot options?

Thank you, I did with openSUSE 11.4 prepared with ImageWriter, Startup Disk Creator flopped.

But I still can't get the machine to [resume by keyboard]("http://ubuntuforums.org/showpost.php?p=11447487&postcount=7").

---

