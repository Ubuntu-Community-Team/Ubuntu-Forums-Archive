---
title: "NTFS USB Hard Drive Unexpectedly Unmounts"
date: 2010-02-05
forum: General Help
---

### Post by Icarus315 on 2010-02-05
Looking for some leads with this post.  I recently updated to Kernel 2.6.32.7 available from the: [Mainline]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").  The reason I have done this is because it corrects an error that prevents my web-cam from functioning (Microsoft VX-3000).  So, with this kernel I have a functioning web-cam *but* I have noticed now that my USB Hard Drive intermittently now unmounts.  I am unable to remount the device without rebooting Ubuntu.  The drive was mounting dirty but installing NTFSProgs and running NTFSfix was the solution for that.  I have disabled power management completely on my machine by editing /etc/default/acpi-support and changing SUSPEND_METHODS to "none" and both ACPI_SLEEP and ACPI_HIBERNATE to false.  This seems to have made the USB hard drive take longer before it unmounts but it does still unmount.  Also as a GRUB2 boot option I have tried acpi=off but this also disabled my usb keyboard and mouse and my BIOS isn't flexible enough to work around that so I cannot use that option.  With these things in mind are there any other avenues I could pursue and things I could try?  Thank you in advance for any advice.

Edit: It may not be "unmounting" it just disappears.  Also, I could try to whitelist the USB controller in /etc/default/acpi-support if I knew how to find out what it was called but I do not know how to do that.. Yet ;)!

Edit2: I moved the physical plug to another slot where it connects on the computer.  If this disconnects again I'll swap out the cable.  If it disconnects again..  I'll go buy a huge 1TB internal sATA and call it a day. ~;)

---

### Post by Icarus315 on 2010-02-06
Did it again.  On shutdown it hung and in text on the screen I saw errors relating to udevd or udevh, I should have noted which one exactly.  Well, leaving it off until something concrete to try and very seriously considering just buying an internal sATA to make my hardware *all* work at the same time.

---

