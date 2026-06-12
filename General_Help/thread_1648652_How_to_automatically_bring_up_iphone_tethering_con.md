---
title: "How to automatically bring up iphone tethering connection and run dhclient?"
date: 2010-12-19
forum: General Help
---

### Post by thehurley on 2010-12-19
Hello,

Ubuntu: 10.10
IOS: 4.2.1

I've installed ipheth-utils using:
```
sudo apt-add-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get install ipheth-utils
```


If I plug my iPhone into my laptop via USB cable, the phone gets mounted but no tethering connection is automatically made.

ubuntu is definitely detecting the insertion and removal of the iphone:

```
thehurley@ubuntu:~$ dmesg | grep iPhone
[ 1823.531139] ipheth 2-1:4.2: Apple iPhone USB Ethernet device attached
[ 2050.648102] ipheth 2-1:4.2: Apple iPhone USB Ethernet now disconnected
```


I can manually configure ubuntu to tether with my iphone to use it's internet connection like this:

```
sudo ifconfig wwan0 up
sudo dhclient
```

Does anyone know how to make internet connection tethering happen automatically?

Thanks

---

### Post by thehurley on 2010-12-24
Figured it out.  Simply add the following to /etc/network/interfaces  

```

auto wwan0
iface wwan0 inet dhcp

```

Once that's done and everything else is configured correctly, when you tether your iPhone the wwan0 interface will come up automatically.

---

### Post by vcrpex on 2011-06-20
thanks thehurley.
I was trying to tether my iphone 3gs with my netbook on maverick. your manual configuration and the instructions to add that to the interface work for me as well.

thank you.

---

