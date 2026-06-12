---
title: "ThinClients : error when running ltsp-build-client"
date: 2006-03-21
forum: General Help
---

### Post by angelot on 2006-03-21
I'm trying to set up a ltsp-server on my ubuntu 5.10 computer using [https://wiki.ubuntu.com/ThinClientHowto](https://wiki.ubuntu.com/ThinClientHowto) and [https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT) guides.

I've got my secondary network-card and a dhcp3-server up and running on eth1.

Then I get to "Build the thin client runtime environment" and I run: ```
$ sudo ltsp-build-client
```
Everything are downloaded and installed, but when I examine the output I find the following errors:```
Setting up nbd-client (2.7.4-1) ...
Stopping NBD client process:
umounting all filesystems for nbd-blockdevices...
Invoking swapoff on all 'nb*' files in /dev...
Disconnecting ...
Can not open NBD: No such file or directory
ERROR: Module nbd does not exist in /proc/modules
nbd-client.
Starting NBD client process: FATAL: Could not load /lib/modules/2.6.12-10-386/modules.dep: No such file or directory
Connecting...Activating...
nbd-client.
```
and ```
Setting up xserver-xorg (6.8.2-77) ...
pcilib: Cannot open /sys/bus/pci/devices
xserver-xorg config warning: failed to infer keyboard layout from layout/lang
   '--nb_NO'
```
Well, it's FATAL, and I guess I'll have to do something with it to get it to work - but I don't know how.

I've finished both guides, but I haven't tried to boot up any thinclients yet.

How can I fix this error?

---

