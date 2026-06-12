---
title: "VPNs"
date: 2010-09-25
forum: General Help
---

### Post by deviator on 2010-09-25
hello.

i'm trying to setup a vpn server so i can use my computer via phone.

my phone only supports pptp, l2tp and l2tp/ipsec psk .

i would like to surf the web, browse files etc.

i've been using this guide

[http://cviorel.easyblog.ro/2009/02/09/how-to-set-up-a-vpn-server-on-ubuntu/]("http://cviorel.easyblog.ro/2009/02/09/how-to-set-up-a-vpn-server-on-ubuntu/")

 but get stuck on the part-

c) Finally, disable and re-enable ufw to apply the changes:

sudo ufw disable && sudo ufw enable


i get the error:

ERROR: problem running ufw-init

...so is there any simple way to get a vpn working on this thing?

or at the very least an in-depth guide that covers what would happen if something goes wrong <_<

---

### Post by deviator on 2010-09-26
i've been having problems with my internet connection ever since i edited the files in the link above.

i changed everything back and now it's fine...i really need a legitimate vpn guide. anyone?

---

### Post by deviator on 2010-09-26
so i have downloaded pptpd

i have uncommented

localip mycomputeripaddress
remoteip 192.168.0.4

in

/etc/pptpd.conf


i've also edited 

/etc/ppp/chap-secrets

and put a username server password and * for my ip.

when i try to connect via wifi on my phone, nothing happens.

any ideas?

i followed the vpn guide on these forums here 
[http://ubuntuforums.org/showthread.php?t=826815](http://ubuntuforums.org/showthread.php?t=826815)

---

### Post by deviator on 2010-09-26
i've also tried 

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

and when i get up to adding

## This is the network bridge declaration

## Start these interfaces on boot
auto lo br0

iface lo inet loopback

iface br0 inet static 
  address 192.168.1.10 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 



and restart, my network gets disconnected.

also my /etc/network/interfaces doesn't look like:



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
## This device provides internet access.
iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0
  gateway 192.168.1.1


it just has:

auto lo eth0
iface lo inet loopback

:mad::mad::mad::mad:

---

### Post by deviator on 2010-09-26
ok update,

i cant use openvpn because apparently my phone wont work with ssl

so back to pptpd and why i cant start the server.:mad:

---

### Post by deviator on 2010-10-03
bump

could somebody please direct me to a tut on how to succesfully connect my android phone to my ubuntu pc using pptpd ?

---

### Post by deviator on 2010-10-06
bump? help?

---

