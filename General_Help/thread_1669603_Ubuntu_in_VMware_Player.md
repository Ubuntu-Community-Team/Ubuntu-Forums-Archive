---
title: "Ubuntu in VMware Player?"
date: 2011-01-17
forum: General Help
---

### Post by AXP on 2011-01-17
Hi!

I have a laptop running Windows 7, and am thinking about installing Ubuntu in VMware Player. I started to do it the other day, but got scared when VMware Player asked me how much hard disk space I would like to reserve for Ubuntu. The recommended amount was about 20 gigs.

If I choose to do this, does that mean that 20 gigs are automatically used up? What I mean is, if I were to look at my C: drive in Windows, it says I have 120 gigs of free space. Then I install Ubuntu in VMware Player. If I go back and look at my C: drive in Windows, will it say that I have now 100 gigs instead of 120?

Thank you very much for any help you may be able to give. I appreciate your time and effort! Have a great day/evening/night - wherever you may be ;)

---

### Post by kouter on 2011-01-28
VMWare actually creates a virtual hard drive within your Windows partition, somewhat like Wubi.  VMWare by default should just create the virtual disk, and it will grow in size as you install or download more within the virtual machine.  There are also options to reserve the full disk space for the virtual disk or split it into multiple files - this helps with disk performance and relocation of the guest OS.

---

