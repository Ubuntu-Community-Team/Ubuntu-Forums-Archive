---
title: "How to install madwimax for ubuntu 11.10 i386"
date: 2012-01-30
forum: General Help
---

### Post by teriyaki-89 on 2012-01-30
Hi everybody my thread is not new  i just installed  ubuntu 11.10 and got my wimax modem samsung u200, but i am  stuck with my modem working
i installed madwimax with command  just apt-get install madwimax
when i plug in modem and type madwimax i get 

Device found
Claimed interface
Allocated tap interface: wimax0

but nothing more and the terminal does not close so ip address is not assigned. I tried to create files in /etc/udev/rules.d like this 


# udev rules file for madwimax  supported devices
SUBSYSTEM!="usb|usb_device",  GOTO="madwimax_rules_end"
ACTION!="add", GOTO="madwimax_rules_end"

ATTR{idVendor}=="04e8",  ATTR{idProduct}=="6761", RUN+="//sbin/madwimax -qd  --exact-device=$attr{busnum}/$attr{devnum}"
ATTR{idVendor}=="04e9",  ATTR{idProduct}=="6761", RUN+="//sbin/madwimax -qd  --exact-device=$attr{busnum}/$attr{devnum}"
LABEL="madwimax_rules_end"



and this 




# udev rules file for madwimax  supported devices
SUBSYSTEM!="usb|usb_device",  GOTO="madwimax_rules_end"
ACTION!="add", GOTO="madwimax_rules_end"

ATTR{idVendor}=="04e8",  ATTR{idProduct}=="6761", RUN+="//sbin/madwimax -qdo  --exact-device=$attr{busnum}/$attr{devnum}"
ATTR{idVendor}=="04e9",  ATTR{idProduct}=="6761", RUN+="//sbin/madwimax -qdo  --exact-device=$attr{busnum}/$attr{devnum}"
LABEL="madwimax_rules_end"


So nothing helped. Could anyone help me with this?:confused:

---

### Post by teriyaki-89 on 2012-02-08
now i run madwimax -vv and get output after plugging in Samsung u 200 wimax modem


Network not found.
Network found.
RSSI: -78   CINR: 14.750000   TX Power: 57344   Frequency: 2663000
BSID: 00:00:4f:01:21:6a
State: NEGO   Number: 2   Response: 1
RSSI: -78   CINR: 15.250000   TX Power: 8   Frequency: 2663000
BSID: 00:00:4f:01:21:6a
State: NEGO   Number: 2   Response: 1
RSSI: 4096   CINR: 512.000000   TX Power: 57344   Frequency: 2525000
BSID: 00:00:4f:01:21:6a
State: NEGO   Number: 2   Response: 1


[B]And the interface wimax0 is not present in ifconfig

So why can't it allocate ip? is it a bug or something with dhcp client?[/B]

---

