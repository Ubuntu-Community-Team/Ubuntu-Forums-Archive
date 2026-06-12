---
title: "Fail to run apt-get update"
date: 2010-02-01
forum: General Help
---

### Post by satimis on 2010-02-01
Hi folks,

Host - Debian 5.0 32bit
VM - Ubuntu 9.10 32bit
KVM

On running
$ sudo apt-get update```

err http://hk.archive.ubuntu.com karmic release.gpg
could not resolve 'hk.archive.ubuntu.com'
......

```

The feature System --> Shutdown/Restart/etc. are missing

Please help.  TIA

B.R.
satimis

---

### Post by wojox on 2010-02-01
Try changing servers to a main one. System > Administration > Software Sources.

---

### Post by satimis on 2010-02-02
> **wojox said:**
> Try changing servers to a main one. System > Administration > Software Sources.
Hi,


I know the problem.  bridge-utils is not installed on this VM.  Therefore it can't connect Internet.  I'm trying to run "apt-get update" and then "apt-get install bridge-utils".  Any solution?  Thanks

B.R.
satimis

---

### Post by satimis on 2010-02-02
Hi folks,

Problem solved as follow;

Edit /etc/network/interfaces;
change ```

# The primary network interface
auto eth0
iface eth0 inet manual

```

as ```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

and comment out all bridge items

$ sudo /etc/init.d/networking restart

Run;
- aptitude update
- aptitude upgrade
- aptitude install bridge-utils

Re-edit /etc/network/interfaces and reinstate all previous settings.

$ sudo /etc/init.d/networking restart

Update problem gone.  The network is running at static IP

However the problem of "virt-manager" is still existing


B.R.
satimis

---

