---
title: "E1000e Driver error on 10.04.4"
date: 2012-09-09
forum: General Help
---

### Post by Hazardr on 2012-09-09
Hi There

I have a problem with a network driver on Ubuntu 10.04

I have an Intel® 82579V Gigabit Ethernet Controller onboard controller and Ubuntu cannot seem to find it. I also have a seperate ethernet card which also works on the same driver (e1000e) and that detects perfectly without any problems...

I googled it and found a few solutions so I managed to download the e10003 drivers for the 82579 card...

The problem I am havig is that after installing and then running

rmmod e1000e and then
modprobe e1000e

it picks up the onboard network card, however, after a reboot the network card disappears and I have to do the above 2 commands again for it to work

Any suggestions

the driver I am installing is here:

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller)

This is my motherboard:

[http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh67bl.html](http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh67bl.html)

---

### Post by steeldriver on 2012-09-09
if the driver works OK and it's just failing to load automatically,  then I think that adding it to /etc/modules should be enough to force it to be loaded at boot time - you can either open the file up in an editor (with sudo or gksudo as appropriate) to do that, or just append it from the command line with

```
echo "e1000e" | sudo tee -a /etc/modules
```The tee is just a workaround to give sudo permission to the redirect - you could also do it with 'sudo sh -c ... '

---

### Post by Hazardr on 2012-09-09
I tried the above... its still not working... I cant simply do modprobe e1000e (load the module)... its already loaded but it doesnt work... then I remove module and reload it with the following command

rmmod e1000e && modprobe e1000e and it picks up the eth1 card (which I assigned static IP in /etc/networking/interfaces)

---

### Post by Hazardr on 2012-09-09
also, heres my /etc/udev/rules.d/70-persistent-net.rules

# PCI device 0x8086:0x10d3 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:05:ca:0b:46:d8", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x1503 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:40:f2:ac:2b:13", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


Eth0 works fine... worked even during installation. eth1 detects here but I cannot bring device up... if I try ifup eth1, I get this errors

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.

This is with a static IP specified

/etc/network/interfaces

auto eth1
iface eth1 inet static
        address 10.0.0.11
        netmask 255.255.255.0

---

### Post by Hazardr on 2012-09-09
ok, i one some more research and found a thread which said I need to do this

update-initramfs -u -k all

All solved and working now... apparently it was loading the old driver on bootup

Thanks :)

---

