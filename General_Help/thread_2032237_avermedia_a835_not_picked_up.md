---
title: "avermedia a835 not picked up"
date: 2012-07-23
forum: General Help
---

### Post by qwertyjjj on 2012-07-23
bought an AverMedia a835 but nothing is listed at all in dmesg.
Any ideas what I have to install to get this to work?
It's ub12.10

teevee@teevee-Inspiron-9300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07ca:a835 AVerMedia Technologies, Inc. 
Bus 003 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
teevee@teevee-Inspiron-9300:~$ dmesg | grep -i dvb
teevee@teevee-Inspiron-9300:~$ sudo dmesg | grep -i dvb
[sudo] password for teevee: 
teevee@teevee-Inspiron-9300:~$

---

### Post by qwertyjjj on 2012-07-23
So, I did all this but that didn;t work either:

sudo apt-get install mercurial build-essential linux-headers-`uname -r`
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
wget [http://xgazza.altervista.org/Linux/DVB/](http://xgazza.altervista.org/Linux/DVB/) &#8230; l_Dvb.diff
patch -p1 < patch_TDA18218_AF9015_AF9035_V4l_Dvb.diff
make
sudo make install
cd /lib/firmware
sudo wget [http://xgazza.altervista.org/Linux/DVB/](http://xgazza.altervista.org/Linux/DVB/) &#8230; 9035-01.fw
sudo reboot

as per [http://forum.ubuntu-fr.org/viewtopic.php?id=799061](http://forum.ubuntu-fr.org/viewtopic.php?id=799061)

EDIT:
now running this:
```

 sudo aptitude install libdigest-sha-perl make gcc git patch patchutils libproc-processtable-perl linux-source linux-headers-`uname -r`

git clone git://linuxtv.org/media_build.git
cd media_build 
./build


make allyesconfig
make
sudo make install


cd /lib/firmware
sudo wget http://xgazza.altervista.org/Linux/DVB/dvb-usb-af9035-02.fw

```

---

### Post by qwertyjjj on 2012-07-23
This worked on 12.04

 sudo aptitude install libdigest-sha-perl make gcc git patch patchutils libproc-processtable-perl linux-source linux-headers-`uname -r`

git clone git://linuxtv.org/media_build.git
cd media_build 
./build


make allyesconfig
make
sudo make install


cd /lib/firmware
sudo wget [http://xgazza.altervista.org/Linux/DVB/dvb-usb-af9035-02.fw](http://xgazza.altervista.org/Linux/DVB/dvb-usb-af9035-02.fw)

---

