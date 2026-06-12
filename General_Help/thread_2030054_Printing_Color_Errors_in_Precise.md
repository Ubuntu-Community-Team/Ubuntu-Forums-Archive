---
title: "Printing Color Errors in Precise"
date: 2012-07-20
forum: General Help
---

### Post by Ron O on 2012-07-20
I am running a dual boot with Lucid and the new install of Precise with Gnome Fallback.

With a standard HP inkjet printer (880C), Precise is printing colors that are way off- flesh tones in teal and an overall solarized look etc. If I boot into Lucid and print the same picture, it is perfect, so it is not the printer. 

I have tried what limited printer options I can find, like switching from "from driver" to "color", and the results are the same. Anybody got a clue? Looks like some kind of bug to me.

---

### Post by Scott Baker on 2012-07-20
You'll want to install the " HPLIP toolbox" package, found through synaptic or the software center. This will allow you to tweak you HPs settings to get them correct.

---

### Post by Ron O on 2012-07-20
Thanks. I have the toolbox installed, and when I try to get into any meaningful settings, I get:

Unable to open device hp:/par/DESKJET_880C?device=/dev/parport0.

In the status tab it says: Device Communication error 5012. This seems to be an HPLIP error.The print settings tab in HPLIP has a number of selections like "printout appearance", but nowhere can I find a dropdown to select the driver it's using like in prior Ubuntu releases. I am wondering if HPLIP may BE the problem since the hookup is the old LPT1.  If I uninstalled HPLIP, would Ubuntu fall back on it's own resources and give me a choice of drivers to select from, or would the printer just stop working entirely? (I ask this because I installed ATIs FGLRX video drivers for a Radeon card and the performance got significantly slower and it maxed out the system memory use. The kernel mode drivers work way better.

---

