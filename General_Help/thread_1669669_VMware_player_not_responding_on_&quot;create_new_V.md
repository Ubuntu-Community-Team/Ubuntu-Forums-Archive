---
title: "VMware player not responding on &quot;create new VM&quot;"
date: 2011-01-18
forum: General Help
---

### Post by greko2009 on 2011-01-18
Hi,

I installed VMware player and when i click on "create new VM" then it freezes and no matter how long I wait it doesn't respond.

Any suggestions?

---

### Post by Vigh on 2011-01-18
Is your BIOS set to have virtualization enabled? Try enabling Virtualization and EIST in the BIOS. Im not sure but I think you need a CPU which supports virtualization to be able to use VMWare Player.

---

### Post by greko2009 on 2011-01-18
I can perfectly run it when loading an existing VM.

I cannot create new!

(btw I have a Quad Core CPU)

---

### Post by Vigh on 2011-01-20
do you have your vmware disks in an encrypted folder? this has been known to cause problems, you can solve this by deleting the lck folders from /home/username/vmware/youroperatingsystem/, if they exist, and then copy the disks to an unencrypted data space, an external HDD should be fine provided its USB2, this may or may not help but is useful information, also be careful when changing USB settings it can render the Virtual Machine useless until the settings and/or device is reconnected and reconfigured

failing that, you may need to uninstall vmware and reinstall vmware, you should be able to keep your virtual disks provided they are backed up/stored on an external disk

---

