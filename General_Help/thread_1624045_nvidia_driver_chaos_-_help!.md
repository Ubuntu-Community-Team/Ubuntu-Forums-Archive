---
title: "nvidia driver chaos - help!"
date: 2010-11-17
forum: General Help
---

### Post by tpprynn on 2010-11-17
I've been trying to finish installing a dual boot system for a friend, on a machine I've built. It has a nvidia 7025.630a chipset. When a second stick of memory comes it will have 4gb of ddr3 ram so I've tried ot install 64 bit Linux Mint 9, to no avail.

Because this comes with two kernels, ...21 and ...23 I've decided to try and install 64 bit Kubuntu 10.04 instead and try to get the nvidia driver working, with desktop effects, transparency etc.

So far, with mint 9 KDE, if i try to install the driver before updates it doesn't seem to be able ot find the current driver listed in Hardware Drivers, and if I get any further than that, i.e. after installing all updates, I just get errors when I reboot and the request to reconfigure etc. I have had various Linuxes on my laptop with intel graphics with none of this bother.

Maybe this won't recur with Kubuntu but I'm concerned that if I run updates a kernel will change and I'll be back to sqaure one.

This seems like complete chaos, and yet I've sorted this out in the past on my own pc with Gnome Ubuntu 10.04 with the same chipset - maybe I just haven't managed to retrace my steps. I think I used deb files in the Ubuntu packages sites, not via Synaptic, but I can't remember the procedure.

I need to get this finished in the next three or four hours because I'm somewhere where there's internet but I don't have it at home, otherwise I'll have to download and burn Simply Mepis 8.5 which doesn't seem to be minus the correct drivers.

Hopefully someone can give me clear instructions.  Thanks very much.

---

### Post by uRock on 2010-11-17
It has been my experience that you install updates, restart the system, then install the nvidia driver and all is good thereafter. I have never had to reinstall the driver after a kernel update.

Are you using the LMDE or the ubuntu version of Linux Mint? There is a big difference in how graphics drivers are installed between the two versions.

Here is a list of the steps I take after a new install of Ubuntu,

1. Install the OS,
2. Install updates to include the newest kernel updates,
3. Restart the system, as it usually asks to do,
4. Install my list of programs that I use,
5. Install graphics driver,
6. Smile with a happily running system.

---

