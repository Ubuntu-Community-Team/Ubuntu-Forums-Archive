---
title: "apt-get does not work sources.list"
date: 2011-12-10
forum: General Help
---

### Post by Joern_MSI on 2011-12-10
Hello

Iam using 9.10 as under 10.x my touch is not working yet. 

Trying to install something with apt-get does not work anymore and also software updates as he cannot find a server anymore..

I tried:

sudo apt-get update
sudo apt-get upgrade 

but always the long list of not found sources... What can I do. Need to install subversion.

W: Konnte [http://de.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz) nicht holen  404  Not Found [IP: 141.30.13.20 80]

W: Konnte [http://de.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz) nicht holen  404  Not Found [IP: 141.30.13.20 80]

W: Konnte [http://de.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz) nicht holen  404  Not Found [IP: 141.30.13.20 80]

E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

---

### Post by Elfy on 2011-12-10
9.10 was end of life in April. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by westie457 on 2011-12-10
Hello you might get better results if you change to a different server. 

Also you will not get any security updates neither will your program versions be updated as 9.10 is no longer supported (since April this year).

We will attempt to get your touchpad working.

Load up your newer version open a terminal and post the output of ```
lspci
```

Thank you.

---

### Post by Joern_MSI on 2011-12-10
Hello thanks for the quick feedback.

this is the output of 

joern@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 Network controller: RaLink RT2860

**This was the way I made it running under 9.04/ 9.10:**

(Iam not an expert but collected that from some post until it worked finally)

Just to use the touchscreen you first have to change the resolution in Xorg.conf to 1366x768. To calibrate it you can use "Touchscreen calibration", note down the values and enter them by hand in the 50-ideaco.fdi file.

sudo aptitude update;
sudo aptitude upgrade -y;
sudo aptitude install xserver-xorg-input-evtouch -y;
mkdir ~/ae1900;
cd ~/ae1900;
wget [http://www.chemisus.com/files/ae1900/xorg.conf](http://www.chemisus.com/files/ae1900/xorg.conf)
wget [http://www.chemisus.com/files/ae1900/50-ideaco.fdi](http://www.chemisus.com/files/ae1900/50-ideaco.fdi)
sudo cp -b xorg.conf /etc/X11/xorg.conf
sudo cp 50-ideaco.fdi /etc/hal/fdi/policy/
sudo shutdown -r now;

update parameters in: 

 /etc/hal/fdi/policy/50-ideaco.fdi
 /etc/evtouch/config

---

