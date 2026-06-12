---
title: "Upgrading from 8.04(lts) to 10.04(lts) Failure"
date: 2010-09-03
forum: General Help
---

### Post by raydon27 on 2010-09-03
Hi,

I'm attempting to upgrade my Ubuntu 8.04 VPS to 10.04 and I'm currently having some trouble with the final stages of the installation.

This is a section of the output I get (seems to be the bit that is going wrong):

```
...
Checking init scripts...
WARNING: this version of the GNU libc requires kernel version
2.6.18 or later. Please upgrade your kernel before installing
glibc.

The installation of a 2.6 kernel _could_ ask you to install a new libc
first, this is NOT a bug, and should *NOT* be reported. In that case,
please add lenny sources to your /etc/apt/sources.list and run:
  apt-get install -t lenny linux-image-2.6
Then reboot into this new kernel, and proceed with your upgrade
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.2_amd64.deb
Exception during pm.DoInstall():  E:Sub-process /usr/bin/dpkg returned an error code (1)

Could not install the upgrades 

The upgrade is now aborted. Your system could be in an unusable 
state. A recovery will run now (dpkg --configure -a). 

Please report this bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bug report. 
E:Sub-process /usr/bin/dpkg returned an error code (1) 

dpkg: dependency problems prevent configuration of locales:
 locales depends on libc6 (>= 2.9-0ubuntu10) | libc6.1 (>= 2.9-0ubuntu10); however:
  Version of libc6 on system is 2.7-10ubuntu6.
  Package libc6.1 is not installed.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Upgrade complete 

The upgrade is completed but there were errors during the upgrade 
process. 

```

Any ideas about how I would go about fixing this?

Thanks
:D

P.S. I don't mind doing another fresh upgrade from the initial 8.04. So the problem is just how to prevent these errors from coming up again.

---

### Post by bobcollard on 2010-09-03
You are trying too big a leap for an upgrade.  The advised way to do it is backup your home folder and Fresh Install Ubuntu 10.04.

---

### Post by raydon27 on 2010-09-04
I am following the guide from [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) which I believe states that you can upgrade from 8.04 LTS to 10.04 LTS.

However, how would I do a fresh 10.04 installation using only the command line (as this is a VPS)?

Once again thanks for the help
;)

---

### Post by bobcollard on 2010-09-04
> **raydon27 said:**
> I am following the guide from [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) which I believe states that you can upgrade from 8.04 LTS to 10.04 LTS.

However, how would I do a fresh 10.04 installation using only the command line (as this is a VPS)?

Once again thanks for the help
;)
Sorry, know nothing of a Virtual Private Server.  I'd use a Live CD.

---

### Post by raydon27 on 2010-09-04
I dont actually have physical access to the machine, so i'm not able to use a cd ^^, thats why I was trying to get the upgrade to work xD.

Thanks for your help anyway ;)

---

### Post by QLee on 2010-09-04
[QUOTE=raydon27]
I'm attempting to upgrade my Ubuntu 8.04 VPS to 10.04 and I'm currently having some trouble with the final stages of the installation.

This is a section of the output I get (seems to be the bit that is going wrong):

```
...
Checking init scripts...
WARNING: this version of the GNU libc requires kernel version
2.6.18 or later. Please upgrade your kernel before installing
glibc.
...
```Any ideas about how I would go about fixing this?
...[/QUOTE]

Does that warning suggest anything?

Are you using a kernel on 8.04 with a version of less that 2.6.18? Did you remember to upgrade 8.04 fully before starting to do the upgrade to 10.04?

---

### Post by raydon27 on 2010-09-04
If I run uname -r I get the following:

```
2.6.9-023stab052.4-smp
```

So I believe that I need to update the kernel?

If I perform an 'apt-get update' and run the 'apt-cache search linux-image' command: 


```
alsa-base - ALSA driver configuration files
linux-image-2.6.24-16-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-16-server - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-16-generic - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-16-server - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-16-openvz - Linux kernel image for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-image-2.6.24-16-rt - Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.3-rt3)
linux-image-2.6.24-16-xen - Linux kernel image for version 2.6.24 on This kernel can be used for Xen dom0 and domU
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
virtualbox-ose-modules-2.6.24-16-generic - virtualbox-ose module for linux-image-2.6.24-16-generic
virtualbox-ose-modules-2.6.24-16-openvz - virtualbox-ose module for linux-image-2.6.24-16-openvz
virtualbox-ose-modules-2.6.24-16-rt - virtualbox-ose module for linux-image-2.6.24-16-rt
virtualbox-ose-modules-2.6.24-16-server - virtualbox-ose modules for linux-image-2.6.24-16-server
linux-image - Generic Linux kernel image.
linux-image-2.6.24-24-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-24-server - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-25-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-25-server - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-26-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-26-server - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-27-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-27-openvz - Linux kernel image for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-image-2.6.24-27-rt - Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.7-rt27)
linux-image-2.6.24-27-server - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-27-xen - Linux kernel image for version 2.6.24 on This kernel can be used for Xen dom0 and domU
linux-image-2.6.24-28-generic - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-2.6.24-28-server - Linux kernel image for version 2.6.24 on x86/x86_64
linux-image-amd64-generic - Upgrade dummy package. Can be removed
linux-image-amd64-k8 - Upgrade dummy package. Can be removed
linux-image-amd64-server - Upgrade dummy package. Can be removed
linux-image-amd64-xeon - Upgrade dummy package. Can be removed
linux-image-debug-2.6.24-24-generic - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-24-server - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-25-generic - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-25-server - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-26-generic - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-26-server - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-27-generic - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-27-server - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-28-generic - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-2.6.24-28-server - Linux kernel debug image for version 2.6.24 on x86/x86_64
linux-image-debug-generic - Linux kernel debug image for generic kernel image
linux-image-debug-server - Linux kernel debug image for server kernel image
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-2.6.24-24-openvz - Linux kernel image for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-image-2.6.24-24-rt - Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.7-rt27)
linux-image-2.6.24-24-xen - Linux kernel image for version 2.6.24 on This kernel can be used for Xen dom0 and domU
linux-image-2.6.24-25-openvz - Linux kernel image for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-image-2.6.24-25-rt - Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.7-rt27)
linux-image-2.6.24-25-xen - Linux kernel image for version 2.6.24 on This kernel can be used for Xen dom0 and domU
linux-image-2.6.24-26-openvz - Linux kernel image for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-image-2.6.24-26-rt - Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.7-rt27)
linux-image-2.6.24-26-xen - Linux kernel image for version 2.6.24 on This kernel can be used for Xen dom0 and domU
linux-image-2.6.24-28-openvz - Linux kernel image for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-image-2.6.24-28-rt - Linux kernel image for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.7-rt27)
linux-image-2.6.24-28-xen - Linux kernel image for version 2.6.24 on This kernel can be used for Xen dom0 and domU
linux-image-openvz - Real time Linux kernel image
linux-image-rt - Real time Linux kernel image
linux-image-xen - Real time Linux kernel image
virtualbox-ose-modules-2.6.24-18-generic - virtualbox-ose module for linux-image-2.6.24-18-generic
virtualbox-ose-modules-2.6.24-18-openvz - virtualbox-ose module for linux-image-2.6.24-18-openvz
virtualbox-ose-modules-2.6.24-18-rt - virtualbox-ose module for linux-image-2.6.24-18-rt
virtualbox-ose-modules-2.6.24-18-server - virtualbox-ose modules for linux-image-2.6.24-18-server
virtualbox-ose-modules-2.6.24-19-generic - virtualbox-ose module for linux-image-2.6.24-19-generic
virtualbox-ose-modules-2.6.24-19-openvz - virtualbox-ose module for linux-image-2.6.24-19-openvz
virtualbox-ose-modules-2.6.24-19-rt - virtualbox-ose module for linux-image-2.6.24-19-rt
virtualbox-ose-modules-2.6.24-19-server - virtualbox-ose modules for linux-image-2.6.24-19-server
virtualbox-ose-modules-2.6.24-20-generic - virtualbox-ose module for linux-image-2.6.24-20-generic
virtualbox-ose-modules-2.6.24-20-openvz - virtualbox-ose module for linux-image-2.6.24-20-openvz
virtualbox-ose-modules-2.6.24-20-rt - virtualbox-ose module for linux-image-2.6.24-20-rt
virtualbox-ose-modules-2.6.24-20-server - virtualbox-ose modules for linux-image-2.6.24-20-server
virtualbox-ose-modules-2.6.24-21-generic - virtualbox-ose module for linux-image-2.6.24-21-generic
virtualbox-ose-modules-2.6.24-21-openvz - virtualbox-ose module for linux-image-2.6.24-21-openvz
virtualbox-ose-modules-2.6.24-21-rt - virtualbox-ose module for linux-image-2.6.24-21-rt
virtualbox-ose-modules-2.6.24-21-server - virtualbox-ose modules for linux-image-2.6.24-21-server
virtualbox-ose-modules-2.6.24-23-generic - virtualbox-ose module for linux-image-2.6.24-23-generic
virtualbox-ose-modules-2.6.24-23-openvz - virtualbox-ose module for linux-image-2.6.24-23-openvz
virtualbox-ose-modules-2.6.24-23-rt - virtualbox-ose module for linux-image-2.6.24-23-rt
virtualbox-ose-modules-2.6.24-23-server - virtualbox-ose modules for linux-image-2.6.24-23-server
virtualbox-ose-modules-2.6.24-24-generic - virtualbox-ose module for linux-image-2.6.24-24-generic
virtualbox-ose-modules-2.6.24-24-openvz - virtualbox-ose module for linux-image-2.6.24-24-openvz
virtualbox-ose-modules-2.6.24-24-rt - virtualbox-ose module for linux-image-2.6.24-24-rt
virtualbox-ose-modules-2.6.24-24-server - virtualbox-ose modules for linux-image-2.6.24-24-server
virtualbox-ose-modules-2.6.24-25-generic - virtualbox-ose module for linux-image-2.6.24-25-generic
virtualbox-ose-modules-2.6.24-25-openvz - virtualbox-ose module for linux-image-2.6.24-25-openvz
virtualbox-ose-modules-2.6.24-25-rt - virtualbox-ose module for linux-image-2.6.24-25-rt
virtualbox-ose-modules-2.6.24-25-server - virtualbox-ose modules for linux-image-2.6.24-25-server
virtualbox-ose-modules-2.6.24-26-generic - virtualbox-ose module for linux-image-2.6.24-26-generic
virtualbox-ose-modules-2.6.24-26-openvz - virtualbox-ose module for linux-image-2.6.24-26-openvz
virtualbox-ose-modules-2.6.24-26-rt - virtualbox-ose module for linux-image-2.6.24-26-rt
virtualbox-ose-modules-2.6.24-26-server - virtualbox-ose modules for linux-image-2.6.24-26-server
virtualbox-ose-modules-2.6.24-27-generic - virtualbox-ose module for linux-image-2.6.24-27-generic
virtualbox-ose-modules-2.6.24-27-openvz - virtualbox-ose module for linux-image-2.6.24-27-openvz
virtualbox-ose-modules-2.6.24-27-rt - virtualbox-ose module for linux-image-2.6.24-27-rt
virtualbox-ose-modules-2.6.24-27-server - virtualbox-ose modules for linux-image-2.6.24-27-server
virtualbox-ose-modules-generic - virtualbox-ose module for linux-image-generic
virtualbox-ose-modules-openvz - virtualbox-ose module for linux-image-openvz
virtualbox-ose-modules-rt - virtualbox-ose module for linux-image-rt
virtualbox-ose-modules-server - virtualbox-ose module for linux-image-server

```

.. as I am running a server I would want to use 'linux-image-2.6.24-26-server'?

from which I would run:

```
apt-get install linux-image-2.6.24-26-server
```

Is this the correct way to upgrade the kernel?

Again any help would be appreciated :)

---

### Post by satish_j on 2010-09-04
You need to update as well as upgrade 8.04 first so that there will remain no unmet dependencies..
However,my experience was very bad..Even after fully upgrading my 8.04 system,i was not able to upgrade to 10.04..I tried googling a lot only to find scores of others facing similar upgrading issues..
You can try it,but my suggestion would be:After upgrading 8.04,if you face any errors at time installing 10.04,then back up your data and do a fresh install of 10.04..
BTW,are you aware that there are some serious bugs in 10.04 that are still not resolved..I am regretting my action of moving to 10.04...

---

### Post by QLee on 2010-09-05
[QUOTE=raydon27]If I run uname -r I get the following:

```
2.6.9-023stab052.4-smp
```So I believe that I need to update the kernel?[/QUOTE]

That's how I would interpret the data in relation to the error report.

[QUOTE=raydon27]If I perform an 'apt-get update' and run the 'apt-cache search linux-image' command: 
...
.. as I am running a server I would want to use 'linux-image-2.6.24-26-server'?

from which I would run:

```
apt-get install linux-image-2.6.24-26-server
```Is this the correct way to upgrade the kernel?

Again any help would be appreciated :)[/QUOTE]

At this point I'm not sure what condition your system is in, it may be the dreaded "mixed" system after a failed upgrade but it may or may not be recoverable. If it was my system, I would try the kernel upgrade, you don't have much to lose at this point. I had a successful upgrade from 8.04 to 10.04 but it was a "plain vanilla" install, no third party apps, and it was fully upgraded previous to trying the version upgrade.

However, I would probably choose the newest available kernel version, unless you know that your system needs the -26 version image.

Good luck!

---

### Post by Jazzy_Jeff on 2010-09-05
For something like this, if you don't have access to the actual computer, I would probably get paid support for the best outcome. That is just me though.

---

### Post by canyon1985 on 2010-09-05
It is my experience that ubuntu can not be upgraded beyond 9.04. I wonder if xen virtualization is better than openvz virtualization where kernel updates are concerned. 1and1 is using a three year old kernel. Its really been a disappointment for me, I like the bleeding edge packages.  Pam and glibc upgrades often brake a openvz vps.

---

