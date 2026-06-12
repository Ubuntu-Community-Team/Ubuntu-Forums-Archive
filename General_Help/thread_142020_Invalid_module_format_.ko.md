---
title: "Invalid module format .ko?"
date: 2006-03-09
forum: General Help
---

### Post by jerinjoy on 2006-03-09
I've installed my vpn client but I'm getting the following error related to invalid module format.

jerinjoy@jj-ubuntu-sys:~$ sudo /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

Does anyone know what is wrong and how I can solve it. I'm new to Ubuntu.

Jerin

---

### Post by adamkane on 2006-03-09
This is over my head, but are you running an Athlon (K7) machine, and do you have the appropriate headers (K7 versus 686) installed?

```

sudo apt-get install linux-headers-k7 linux-image-k7 linux-k7  linux-restricted-modules-k7

``` 

If your installation script (install.sh) calls for linux*-686 packages, then the script may need to be edited slightly to accommodate linux*-k7 packages.

---

### Post by hw-tph on 2006-03-09
If you have built this kernel module locally, make sure you build it using the same compiler as your current kernel. Compare /proc/version and **gcc --version**.


Håkan

---

### Post by jerinjoy on 2006-03-10
i'm running ubuntu on my centrino laptop. i didn't compile the source. The vpn client installation asked me for my source directory when I installed and I pointed it to the headers directory in /usr/src/

---

### Post by Bubbel on 2007-02-07
Got the job done. Seems to originate from two problems:
1: Spaces in the path where the installer "vpn_install" resides, so I moved it to /media/hdb1/cisco.
2: run vpn_uninstall from that directory, before you do vpn_install again.

An extra I've done is removed the subfolder tmp_versions.

That did it for me.:biggrin:

bbl

---

