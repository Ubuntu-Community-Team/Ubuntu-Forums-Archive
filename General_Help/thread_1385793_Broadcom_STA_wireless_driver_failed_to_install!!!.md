---
title: "Broadcom STA wireless driver failed to install!!!"
date: 2010-01-20
forum: General Help
---

### Post by Salesh on 2010-01-20
My Broadcom STA wireless driver has failed to installed.
[B]The error report says that "PLEASE HAVE A LOOK AT THE LOG FILE FOR DETAILS: /var/log/jockey.log
[/B]WHAT SHOULD BE DONE TO GET THE WIRELESS STA driver functional............?????
Gotta see it functiioning back!!!!

---

### Post by akhilbehl on 2010-01-24
first of all you should look at the log.. and tell us here what the log says.

you can open a terminal

Applications > Accessories > Terminal

type 

cat /var/log/jockey.log and post it here

---

### Post by Jimtheplanner on 2010-01-24
Hi Salesh,

I've had issues with broadcom STA. I find that it will install in about 1 out of 4 installs.

Ok first off.... removals either in terminal or synaptic (your choice)

If synaptic then remove > BCMWL-kernel-source

Then re-boot

Then make sure everything is up-to-date with 

> sudo apt-get update

and 

> sudo apt-get upgrade

After this Jockey should work for you so install the driver via hardware drivers. If not you can install BCMWL-kernel-source from synaptic

Jim

---

### Post by KaOS-bEat on 2010-02-02
I had the same problem after upgrading form karmic to lucid-beta2


This worked for me 


Thanks!

---

### Post by mrnatas20 on 2010-12-23
I have tried this solution, but to no avail! I have a Dell Inspiron 1525 with 10.10 on it, and have been having wireless issues recently. I have tried many other solutions for the b43 driver (from what I've gleaned an older and buggier driver) for my wireless card, but none of these solutions have worked for me.  When I attempt to install the STA driver after performing the above instructions, an error occurs, telling me to look at the jockey.log   

The output from 
```
 lspci -vvnn | grep 14e4

```

is 

```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

and the output from the log is (rather long):

2010-12-23 15:47:03,656 DEBUG: Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 198307 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.36-020636rc7-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.36-020636rc7-generic

2010-12-23 15:47:03,902 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-12-23 15:47:03,903 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-12-23 15:47:04,036 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-23 15:47:06,819 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-23 15:47:06,868 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-23 15:47:06,941 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-12-23 15:47:08,395 DEBUG: Shutting down


In synaptic, I do have bcmwl-kernel-source reinstalled, wl installed, and firmware-b43-installer and firmware-b43l-lpphy-installer uninstalled. (from all my solution attempts these are relevant / problematic drivers).

Could someone help me? I do have ethernet access working correctly, and I have been using 10.10 for a month or two (I had a wireless problem before but righted itself somehow).  

Note: I have also been playing with virtualbox, had a nice win7 client setup, and then started getting kernel errors, whereupon I started trying to fix them (also to no avail), so I ended up uninstalling virtualbox.  This was a decent amount of time before my wireless stopped working.

Thanks

---

### Post by uniquexplosion on 2011-06-13
I think this might help ;) (not spam, real solution that worked for me)

[http://alexferreirascode.blogspot.com/2011/06/broadcom-sta-wireless-driver-jockeylog.html](http://alexferreirascode.blogspot.com/2011/06/broadcom-sta-wireless-driver-jockeylog.html)

---

### Post by whaa on 2011-10-11
> **Jimtheplanner said:**
> Hi Salesh,

I've had issues with broadcom STA. I find that it will install in about 1 out of 4 installs.

Ok first off.... removals either in terminal or synaptic (your choice)

If synaptic then remove 

Then re-boot

Then make sure everything is up-to-date with 



and 



After this Jockey should work for you so install the driver via hardware drivers. If not you can install BCMWL-kernel-source from synaptic

Jim

Had the same problem after upgrading to Oneiric yesterday.

Your solution worked perfectly. Thanks Jim.

-
Ilker

---

