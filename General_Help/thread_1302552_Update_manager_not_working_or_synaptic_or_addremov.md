---
title: "Update manager not working or synaptic or add/remove programs"
date: 2009-10-27
forum: General Help
---

### Post by matthewh427 on 2009-10-27
Hi this is the error message I get when I try and open the synaptic package manager or update manager or add/remove programs.


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I have not changed any settings or anything can anyone help me please.

---

### Post by darkksyde on 2009-10-27
Try going to System > Administration > Software Sources and choose a different update mirror

---

### Post by ShapeShiftme on 2009-10-27
Did you recently try install something and it gave you an error through it. 

That happened to me a while back. All i did was try install a package through console and it gave me an option to finish the install. after i did that everyhting worked fine

---

### Post by matthewh427 on 2009-10-27
> **darkksyde said:**
> Try going to System > Administration > Software Sources and choose a different update mirror

I tried changing the download option to main server from the UK one and it didn't help.

The only changes I have made recently was to remove Skype I got from the Mediabuntu repository and install the new Skype beta from there website.

---

### Post by drs305 on 2009-10-27
> **matthewh427 said:**
> Hi this is the error message I get when I try and open the synaptic package manager or update manager or add/remove programs.


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I have not changed any settings or anything can anyone help me please.

Open Synaptic or Software Sources. Go to Settings, Repositories. Note which ones you have selected in the Ubuntu Software and Third Party tabs. Deselect (untick) them, then reselect them, then Reload. That should force your system to fetch the repository lists again, hopefully getting rid of whichever one(s) has/have the error.

It's probably just the "partner" list but it's easier just to reload them all.

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by matthewh427 on 2009-10-27
> **drs305 said:**
> Open Synaptic or Software Sources. Go to Settings, Repositories. Note which ones you have selected in the Ubuntu Software and Third Party tabs. Deselect (untick) them, then reselect them, then Reload. That should force your system to fetch the repository lists again, hopefully getting rid of whichever one(s) has/have the error.

It's probably just the "partner" list but it's easier just to reload them all.

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

That worked thanks a lot :D

---

