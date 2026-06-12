---
title: "Geforce 4 Help!"
date: 2009-07-22
forum: General Help
---

### Post by Pr0_newbie on 2009-07-22
I'm NEW to Linux.  Just thought I'd give it a try.   I got Ubuntu installled (beside Windows), got Limewire installed, etc.


My hangup is installing video drivers!   I'm stuck in 800x600 resolution and it sucks!  I have a Geforce 4 TI card (I know it's older than the hills).

I tried going to System/Admin/Hardware Drivers in Ubuntu to update but it  just keeps saying 'searching' or it times out.

I realize I had a outdated card, but can anyone help ?


Thanks

Pro

---

### Post by Whiffle on 2009-07-22
I'm pretty sure you're going to need the nvidia 96 series driver for that card, 

Go to

System > Administration > Synaptic Package Manager.

When it opens, put "nvidia-glx-96" in the search box, search, and then check the box next to the one that says "nvidia-glx-96", you don't need the "-dev" one.  Then click the Apply button and let it do its thing.  I think thats all you need, although you might need to run "sudo nvidia-xconfig" in a terminal when you're done.

---

### Post by Pr0_newbie on 2009-07-23
I'll give it a shot, thanks for the tip!

---

### Post by Pr0_newbie on 2009-07-24
> **Whiffle said:**
> I'm pretty sure you're going to need the nvidia 96 series driver for that card, 

Go to

System > Administration > Synaptic Package Manager.

When it opens, put "nvidia-glx-96" in the search box, search, and then check the box next to the one that says "nvidia-glx-96", you don't need the "-dev" one.  Then click the Apply button and let it do its thing.  I think thats all you need, although you might need to run "sudo nvidia-xconfig" in a terminal when you're done.

Worked great!  No need for the nvidia-xconfig.  Thanks for the help!!!!!

---

