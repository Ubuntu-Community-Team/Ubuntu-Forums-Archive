---
title: "Not detecting HDD during install"
date: 2011-06-29
forum: General Help
---

### Post by brandon89 on 2011-06-29
I'm trying install Ubuntu from a USB drive, but when I get to the screen where it says "Must have 4.6GB of space available, ect, ect" I don't have a green check mark by it.  How do I get Ubuntu to recognize that I do actually have more than 4.6GB of space and allow me to install?

---

### Post by Mark Phelps on 2011-06-29
Next time, use the Try It option, instead of install.

Once into Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.

If you already have 4 primary partitions allocated to your hard drive, Ubuntu won't give you the option to create another -- so it may look like it does not see the drive.

---

### Post by brandon89 on 2011-06-29
When I get home I'll try this, but the HDD is brand new.  I was just going to install Ubuntu immediately, but it didn't recognize that I had free space then either.  I then installed Windows 7 to make sure that the HDD wasn't dead, but Windows installed just fine so I'm not sure whats wrong.  When I load up the live disc (tried from both USB and CD) Ubuntu only says I have like 3GB of space when I should have about 450GB...

---

### Post by brandon89 on 2011-06-29
Just to post back, apparently the HDD wasn't being detected because it was plugged into the SATA 3 port.  I just plugged it into the SATA 2 port and installation went fine.

---

