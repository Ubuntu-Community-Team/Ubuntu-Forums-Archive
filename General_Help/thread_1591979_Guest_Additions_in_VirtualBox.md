---
title: "Guest Additions in VirtualBox ??"
date: 2010-10-10
forum: General Help
---

### Post by OllieGab on 2010-10-10
Basic (silly perhaps?) question!
I've installed a guest OS (openSuse) in VitualBox (using 10.4) and when installing the guest "addtions"; are they installed in Ubuntu, in the guest OS itself or is it perhaps just a plug-in to VB?


I've downloaded the Guest Additions but when trying to install it I just get the following error message:

Unable to mount the CD/DVD image /home/joebloggs/.VirtualBox/VBoxGuestAdditions_3.1.6.iso on the machine openSuse. Would you like to force mounting of this medium?
Could not mount the media/drive '/home/joebloggs/.VirtualBox/VBoxGuestAdditions_3.1.6.iso' (VERR_PDM_MEDIA_LOCKED).

Any suggestions?
Cheers Ollie

---

### Post by techdude3177 on 2010-10-10
The virtualbox guest addon is installed on the VM to interact with the host machine.
From the VM window you should be able to go to Devices > Install Guest Additions... and it should mount the CD for you on the VM.

---

### Post by OllieGab on 2010-10-10
> **techdude3177 said:**
> The virtualbox guest addon is installed on the VM to interact with the host machine.
From the VM window you should be able to go to Devices > Install Guest Additions... and it should mount the CD for you on the VM.

Well, that's when I get the error message I mentioned...and I don't really know how to go from there...

---

