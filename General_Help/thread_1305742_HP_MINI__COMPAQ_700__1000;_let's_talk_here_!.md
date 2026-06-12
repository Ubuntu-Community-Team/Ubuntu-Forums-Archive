---
title: "HP MINI  COMPAQ 700 / 1000; let's talk here !"
date: 2009-10-30
forum: General Help
---

### Post by frenchn00b on 2009-10-30
Hi guys, 

Ubuntu and HP MINI COMPAQ 700 / 1000!  

I advice to use JWM with it.
> apt-get install jwm
cp /usr/share/jwm/xsessions/Jwm.desktop /usr/share/xsessions/


Let's talk here. 

If you are reading this, it means you already managed to install linux, and get internet via wlan or lan. 

You like this HP MINI? hp mini 700 / 1000, is it a good machine?

[B]My ethernet cable eth0 works with this debian distro: [http://cdimage.debian.org/cdimage/daily-builds/daily/20091206-5/i386/iso-cd/debian-testing-i386-netinst.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/20091206-5/i386/iso-cd/debian-testing-i386-netinst.iso)
my wifi and bluetooth too: check below[/B]

Greetings

---

### Post by frenchn00b on 2009-10-30
[http://welcome.hp.com/country/us/en/support/prod_info.html](http://welcome.hp.com/country/us/en/support/prod_info.html) 
a question, where are the windows drivers? 
seems not existing :(

---

### Post by frenchn00b on 2009-11-08
how to make wifi working :

[CODE
lsmod  | grep "b43\|ssb\|wl"

echo continue ?
####read lkjdfllksdfl

rmmod b43
rmmod ssb
rmmod wl

#echo blacklist?
###read lkjklfjdsfd

#echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
#echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf


echo modprobing



modprobe lib80211
insmod wl.ko

ifconfig
iwlist
iwconfig


exit
exit 0
exit -1

][/CODE]

here are the files in the folder:
built-in.o                                 hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz  lib       Module.markers  Module.symvers  src    wl.mod.c  wl.o
howtoinstallbluetoohandwirelesshpmini.txt  install-remove-theb43mod.sh                Makefile  modules.order   README.txt      wl.ko  wl.mod.o

---

### Post by frenchn00b on 2009-12-08
here is the file with the WIFI installer for hp mini:
up to 10 downloads and it is gone. 
[http://rapidshare.com/files/317923310/wifi-hpmini-install.tar.gz.html](http://rapidshare.com/files/317923310/wifi-hpmini-install.tar.gz.html)

---

