---
title: "can't install flash plugin"
date: 2012-04-19
forum: General Help
---

### Post by jcdenton_riseup on 2012-04-19
I get this message whenever I try to install it: "Check if you are using third party repositories. If so disable them, since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install -f"

I tried disabling third party repositories but nothing changed. And the terminal command gave me this message: "E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

Anyone know how to sort this out?

---

### Post by HiImTye on 2012-04-19
close other package managers (synaptic, ubuntu software center, update manager) and it should fix your problem

---

### Post by jcdenton_riseup on 2012-04-20
> **HiImTye said:**
> close other package managers (synaptic, ubuntu software center, update manager) and it should fix your problem

Not sure if that's what you meant, but I closed 'update notifier' through the 'system monitor' ('synaptic' and 'ubuntu software center' weren't running at the time) and tried 'sudo apt-get install -f' again. Here's what I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flashplugin
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  adobe-flashplugin
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/6,591kB of archives.
After this operation, 17.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 151812 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_11.2.202.233-0lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/iceweasel/plugins', which is also in package iceweasel 0:1.5.0.8pre-2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_11.2.202.233-0lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jcdenton_riseup on 2012-04-22
Fixed it.

Here's what I did: I removed the 'adobe-flash-properties-gtk' package through 'synaptic' because it was broken -> removed 'iceweasel' (which I no longer use) -> upgraded all the packages through 'apt-get upgrade' -> installed the latest flash.

---

