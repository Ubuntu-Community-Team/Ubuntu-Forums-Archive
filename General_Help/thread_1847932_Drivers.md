---
title: "Drivers?"
date: 2011-09-21
forum: General Help
---

### Post by android272 on 2011-09-21
why is it that when I go to update my drivers though additional drivers the only drivers that ever come up are my video drivers. should I not have other drivers then just my video card (e.g. wifi card, projectors, any thing else that needs drivers to work.) do other drivers drivers install through the update manager.

---

### Post by MG&amp;TL on 2011-09-21
The only drivers you need to install are proprietary ones which linux does not have access to; if they're open source or have been imported in some other way, they are already installed.

Wifi drivers aren't often required, mostly they have been written or ported. Projectors I don't know about, but since it's a stand-alone unit connected by a lead with its own buttons, I guess the SCART driver(?) does well enough.

---

### Post by patryk77 on 2011-09-21
Most drivers in Linux are Open Source, and included directly in the Kernel.

Additional drivers is for Closed Source drivers written by NVidia or ATI, possibly some others, which Linux Users are not free to modify.

Generally, Open Source drivers are better for the community, but certain things like graphic cards are quite complex, which is why you need to enable the proprietary drivers to use 3D acceleration and other features.

I also only have the Nvidia drivers in there.

Edit: Projectors receive input as a VGA or DVI signal; the video card does the processing and as such they don't need drivers.

---

### Post by Robbie80 on 2011-09-21
Linux has its drivers built into the kernel itself, when Ubuntu Software Center shows you available drivers, they are proprietary drivers that are not built into the kernel, but they may work better than the default drivers.
 If USC does not show you drivers for a particular device, say a wifi card, then the default linux kernel drivers are the only ones in the repo and are already installed on your system, unless it is a device with no known linux driver (like some fingerprint scanners and printers) in that case you are out of luck unless you can build your own.
 Every time you update your system, all the linux kernel and its drivers are updated as are proprietary drivers installed through USC. If you have a device for which Ubuntu doesn't have a driver in their repos for, you may be able to check the manufacturer's web site for a linux/unix driver but you will have to compile the software yourself. 

I hope that helps!

---

