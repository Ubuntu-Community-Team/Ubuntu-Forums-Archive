---
title: "VBox guest additions again........"
date: 2009-12-04
forum: General Help
---

### Post by nichos on 2009-12-04
Hi,
Host XP.
VBox on it.
Upuntu 9.10 installed in VBox  

cannot install again the VBox Linux guest additions.

The Devices guest additions do not work

Chasing my tail with all these from various helps:-

cd /media/cdrom

sudo mount /dev/cdrom  /media/cdrom

sudo sh ./VBoxLinuxAdditions-amd64.run

sudo apt-get install build-essential linux-headers-generic

---

### Post by quixote on 2009-12-05
The standard method is to start the vm, ubuntu in your case, then go to Devices on the virtualbox menu (right above the vm's top edge) and choose "InstallGuestAdditions" at the bottom of the dropdown.  That mounts the "CD" (even though it's probably just an iso on your system).  (You can also mount it before you start the vm, but this is easier, I think.)

Then you can use nautilus to browse the CD.  Double click on "VBoxLinuxAdditions-x86.run" (or VBoxLinuxAdditions-amd64.run if you have  64-bit vm) and choose "run."  For me, for some reason, it wouldn't execute from the command line, but did via nautilus.  Then you restart the vm, and you should be done.

Or have you done all this already and did it not work?

---

### Post by Ocxic on 2009-12-05
type "uname -a" you will get your kernel version
ex: Linux xilti 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64 GNU/Linux
then:
"sudo apt-get install linux-headers-2.6.31-16-generic"

just replace your version number with the one that i have here. and try to install the guest additions again.  the headers are the files that you'll usually need to compile kernel modules.

---

### Post by nichos on 2009-12-06
SOLVED Thanx all,

nothing worked here untill just now updated VBox from 2.1 to 3.1, & reistalled 9.10.

I ouble click on the desktop icon for VB Guest Additions again the 'autorun.sh', & clicked Run.

this time it worked & am on my way.                               ...............nick

---

