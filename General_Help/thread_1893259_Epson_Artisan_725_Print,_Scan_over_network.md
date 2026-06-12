---
title: "Epson Artisan 725 Print, Scan over network"
date: 2011-12-09
forum: General Help
---

### Post by Mega_Mike on 2011-12-09
Got printing, scanning working in Ubuntu 11.10, 64 bit with an Epson 725.  Ubuntu does a good job of installing everything you need to print out of the box by automatically finding and installing the proprietary Epson driver, but scanning thru Simple Scan will get you a **Communication Error**.

To fix you need to get the 3 iScan packages from
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

```
iscan-data_1.13.0-1_all.deb
iscan_2.28.1-3.ltdl7_amd64.deb
iscan-network-nt_1.1.0-2_amd64.deb
```

These were the two commands I needed to run to install in the directory you downloaded the deb files.

```
sudo apt-get install xsltproc
sudo dpkg -i iscan-data_1.13.0-1_all.deb iscan_2.28.1-3.ltdl7_amd64.deb iscan-network-nt_1.1.0-2_amd64.deb
```

Thats it.  Startup Simple Scan and scan away.

---

