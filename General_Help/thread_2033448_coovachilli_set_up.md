---
title: "coovachilli set up"
date: 2012-07-26
forum: General Help
---

### Post by fatboy07 on 2012-07-26
Hello! again I need help regarding coovachilli set up, I'm currently using ubuntu, also I want to know is this coova can be install on other distro? thanks in advance!

---

### Post by 2F4U on 2012-07-26
Since you provide no details about what your problems are, I am just referring to the Wiki documentation:

[https://help.ubuntu.com/community/WifiDocs/CoovaChilli](https://help.ubuntu.com/community/WifiDocs/CoovaChilli)

---

### Post by fatboy07 on 2012-07-26
> **2F4U said:**
> Since you provide no details about what your problems are, I am just referring to the Wiki documentation:

[https://help.ubuntu.com/community/WifiDocs/CoovaChilli](https://help.ubuntu.com/community/WifiDocs/CoovaChilli)

Thanks for the link, I want ot install in to my machine so I can start a captive portal, :)

---

### Post by fatboy07 on 2012-07-26
>    Can I use the system on a Unix-like computer operating system (Linux, FreeBSD, etc.)?
Question 
Can I use the system on a Unix-like computer operating system (Linux, FreeBSD, etc.)?

Answer 
Yes, you don't have to run the system on a router.

All you need to do is to install Coovachilli and set the  Chilli parameters.

Coovachilli is an open source captive portal or wireless LAN access point controller. Binary downloads are available for Redhat, Febora, Debian, Mandrake and OpenWRT. Coovachilli is an ebuild in Gentoo and compiles under FreeBSD. Source code under GPL is available for other platforms.

Use the configuration below for the chilli settings stored in the chilli.conf file: 

 

 

radiusserver1 radius.hotspotsystem.com
radiusserver2 radius2.hotspotsystem.com
radiussecret hotsys123
dhcpif eth1
net 192.168.182.0/24
uamserver [https://customer.hotspotsystem.com/customer/hotspotlogin.php](https://customer.hotspotsystem.com/customer/hotspotlogin.php)
dns1 8.8.8.8
dns2 8.8.8.8
uamsecret hotsys123
uamanydns
radiusnasid YOUROPERATORID_YOURLCOATIONNUMBER
uamhomepage [https://customer.hotspotsystem.com/customer/index.php?operator=YOUROPERATORID_YOURLCOATIONNUMBER](https://customer.hotspotsystem.com/customer/index.php?operator=YOUROPERATORID_YOURLCOATIONNUMBER)
coaport 3799
coanoipcheck
domain key.chillispot.info
uamallowed hotspotsystem.com,customer.hotspotsystem.com
uamallowed 194.149.46.0/24,198.241.128.0/17,66.211.128.0/17,216.113.128.0/17
uamallowed 70.42.128.0/17,128.242.125.0/24,216.52.17.0/24
uamallowed 62.249.232.74,155.136.68.77,155.136.66.34,66.4.128.0/17,66.211.128.0/17,66.235.128.0/17
uamallowed 88.221.136.146,195.228.254.149,195.228.254.152,203.211.140.157,203.211.150.204
uamallowed [www.paypal.com,www.paypalobjects.com](www.paypal.com,www.paypalobjects.com)
uamallowed [www.worldpay.com,select.worldpay.com,secure.ims.worldpay.com,www.rbsworldpay.com,secure.wp3.rbsworldpay.com](www.worldpay.com,select.worldpay.com,secure.ims.worldpay.com,www.rbsworldpay.com,secure.wp3.rbsworldpay.com)
uamallowed [www.hotspotsystem.com,customer.hotspotsystem.com,tech.hotspotsystem.com](www.hotspotsystem.com,customer.hotspotsystem.com,tech.hotspotsystem.com)
uamallowed a1.hotspotsystem.com,a2.hotspotsystem.com,a3.hotspotsystem.com,a4.hotspotsystem.com,a5.hotspotsystem.com,a6.hotspotsystem.comuamallowed a7.hotspotsystem.com,a8.hotspotsystem.com,a9.hotspotsystem.com,a10.hotspotsystem.com
interval 300

Actually this is the reason why I want to setup coovachilli, seems that it works only in ubuntu distro.

---

### Post by soundsticks on 2013-02-26
I did setup the coovachilli but after i run the hotspot i couldn't login to the router page.

---

