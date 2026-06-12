---
title: "Why do kernel upgrades always kill my fglrx"
date: 2011-03-17
forum: General Help
---

### Post by hawthornso23 on 2011-03-17
Every time I get a kernel upgrade it kills my ATI fglrx driver and I have to reinstall it. I understand that for most people this doesn't happen. A kernel update can go through and leave the fglrx driver functioning afterwards. 

Can anyone suggest why my fglrx driver setup is so fragile that it is unable to survive a kernel upgrade. Apart from that everything seems to be working OK in video driver land. I suspect some sort of collateral damage to a config file may have occurred as a result of past epic battles with fglrx.

I'm running Lucid upgraded from Karmic upgraded from Jaunty upgraded from Intrepid. A clean install would no doubt fix the problem. In the meantime I get a lot of practice installing fglrx drivers. I'm pretty efficient at it by now so this is really only a minor inconvenience. I'm not exactly in desperate need. I'm mostly just curious as to why my system behaves differently from the norm.

Any suggestions as to where the issue may lie?

Thanks

---

### Post by lithopsian on 2011-03-17
It could be that you are losing some modules.  Or rather that required modules that are installed by fglrx are not being copied into your new kernel module directory structure.  Do a compare   There is an fglrx kernel module, take a look for it in your existing and a new /lib/modules directory.

---

### Post by kerry_s on 2011-03-17
because the drivers have to match the kernel.

when it's installed, it's to the current running kernel.

so when that happens hold the shift key at boot, which will bring up the menu, select the older kernel & that should get you to gui where you can fix. the fix is usually switching to the open driver, then booting the new kernel, then install the driver.

---

### Post by b0b138 on 2011-03-17
do you have dkms installed?

---

### Post by hawthornso23 on 2011-03-18
> **b0b138 said:**
> do you have dkms installed?

Yes.  Version   2.1.1.2-2fakesync1

Good suggestion though.

---

### Post by hawthornso23 on 2011-03-18
> **kerry_s said:**
> because the drivers have to match the kernel.

when it's installed, it's to the current running kernel.

so when that happens hold the shift key at boot, which will bring up the menu, select the older kernel & that should get you to gui where you can fix. the fix is usually switching to the open driver, then booting the new kernel, then install the driver.


For most people when the kernel is upgraded some magic happens to upgrade the kernel modules to match. That magic seems to be broken on my system.

Reinstalling fglrx is not a problem - as I said I'm pretty well practiced at it. No need to boot to an old kernel - it falls back to the open driver if the proprietary one is unavailable.

---

### Post by hawthornso23 on 2011-03-18
> **lithopsian said:**
> It could be that you are losing some modules.  Or rather that required modules that are installed by fglrx are not being copied into your new kernel module directory structure.  Do a compare   There is an fglrx kernel module, take a look for it in your existing and a new /lib/modules directory.

I'm sure you are right that the kernel modules are not being copied over. I just wonder why it is happening.

---

### Post by mastablasta on 2011-03-18
> **hawthornso23 said:**
> as I said I'm pretty well practiced at it..
 
hmm what do you mean by this? how are your fglrx installed? through the hardware drivers menu? and then enable drivers?

---

### Post by mcduck on 2011-03-18
> **hawthornso23 said:**
> For most people when the kernel is upgraded some magic happens to upgrade the kernel modules to match. That magic seems to be broken on my system.

Reinstalling fglrx is not a problem - as I said I'm pretty well practiced at it. No need to boot to an old kernel - it falls back to the open driver if the proprietary one is unavailable.

Do you have the correct metapackages for your kernel installed?

"linux-generic & linux-headers-generic" or "linux-generic-pae & linux-headers-generic-pae" for 32-bit Ubuntu, or whatever the equivalent packages for 64-bit Ubuntu might be called...

(I haven't used fglrx for a while, so make if there's any other kernel-related packages it needs, like one of the linux-backports-modules -packages, you should also check if you are missing the metapackage for that one)

As the kernel updates are installed alongside the old versions instead of replacing them, having a specific package version will not provide you any updates. Instead these matapackages are sued, they always depend on the latest version of the package they are for, making sure you get the new version during a kernel update.

---

### Post by 3rdalbum on 2011-03-18
If you have installed fglrx from the ATI website, then you will need to reinstall fglrx every time the kernel gets updated; this is because ATI's installer doesn't do the necessary DKMS "magic" to have the driver rebuilt when a new kernel gets installed.

If you install fglrx from the "Additional Drivers" program, Synaptic or Software Center, then these packages should register the driver with DKMS and they'll be rebuilt when a new kernel gets installed.

You should confirm to us how you installed fglrx and if it was from Additional Drivers then we can take it from there and try troubleshooting.

---

### Post by hawthornso23 on 2011-03-19
Doh -  I've got the ATI version installed at the moment.

<facepalm>

sorry for troubling you all. Problem understood.

---

