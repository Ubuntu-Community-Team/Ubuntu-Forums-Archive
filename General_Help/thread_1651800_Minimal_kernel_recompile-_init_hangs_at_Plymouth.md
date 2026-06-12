---
title: "Minimal kernel recompile- init hangs at Plymouth"
date: 2010-12-23
forum: General Help
---

### Post by Ibidem on 2010-12-23
Well, I've been playing around in attempt to see how small a usable kernel I can build.  The theory is that it should mainly be useful for preparing a recovery disk or some such thing; disk drivers and a few network drivers are what goes in.

I built the kernel with the attached config.
It boots, reaches the hdd (if I specify root as /dev/sda5 manually), then dies when it tries to start Plymouth (something about catching a SEGV signal).
What needs to be enabled to run Plymouth?  Alternatively, has anyone managed to remove plymouth from boot on Maverick?
(That would require a modified mountall version, I know.)
I'm using the mainstream kernel 2.6.32.27 sources on Maverick (yes, I know Maverick uses 2.6.35; but this does boot).

Hardware: Wireless-RTL8192SE b/g/n, uses an out-of-tree driver (r8192se_pci, from Realtek; Ubuntu builds in an older version of this driver); r8169 works for ethernet; ATI Radeon Mobility 3200 graphics, AMD Neo X2 cpu; SATA hd in AHCI mode.

---

### Post by jcrazo on 2011-01-19
Same problem i just configured my custom 2.6.37 kernel:

```
$make menuconfig
```built it:

```
$make -j4
```installed it:

```
#make modules_install
``````
#make install
```and updated grub:

```
#update-grub
```and when booting it mounts root and all but hangs before gdm, im not sure what the problem is plymouth or xserver??

---

