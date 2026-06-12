---
title: "How to install ATI Radeon x700 driver"
date: 2010-02-20
forum: General Help
---

### Post by alket on 2010-02-20
I just downloaded ATI Radeon x700 driver from > [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.18&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.18&lang=English)

the file name is

> ati-driver-installer-9-3-x86.x86_64.run

I gave permission as Executing file as program

I run as sudo from terminal but I get this error

> Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-20-generic; make sure that the version is being
correctly set by --iscurrentdistro

---

### Post by jocko on 2010-02-20
That driver is outdated and will not work with a current kernel and xserver. Ati dropped support for your card in april last year, so the open source driver (radeon) is the only one that supports your card on any ubuntu release newer than 8.10.

---

