---
title: "Help converting 64-bit to 32-bit"
date: 2010-02-01
forum: General Help
---

### Post by umakemyheadhurt on 2010-02-01
We've customized Karmic 64-bit installed on a master machine and use fsarchiver to take an image of the entire disk.  It's then easy to set/image new machines the company purchases so they are virtual copies of the master, just with a few slight changes like machine name, etc.

It's working fine for new 64-bit machines, but now they want to put the image on some older 32-bit machines...

Does anyone have an idea of how I could take a complete inventory of all 64-bit packages on the master, drivers, etc... And then install the corresponding 32-bit versions?   Including the kernel also of course.  Any other tips or gotchas for "reverting" to 32-bit?

Thanks

---

### Post by philinux on 2010-02-01
You'll have to make a master on a 32 bit machine. You cant revert.

If you open synaptic and use file>save markings as.

Now when I tried this I had to save to my home folder or it failed to work. Also I had to use a file name like testmarks. It didn't like test. Maybe the filename was too short. It would not save the file to my desktop either.

To reinstall all marked packages use File>Read markings. Point it at your file you saved. Obviously either copy to the clean 32 bit install or usb stick.

You also need to back up the home folder including hidden files and copy this to the new install.

---

