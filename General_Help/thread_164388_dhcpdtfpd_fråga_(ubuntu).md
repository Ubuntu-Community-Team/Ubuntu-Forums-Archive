---
title: "dhcpd/tfpd fråga (ubuntu)"
date: 2006-04-22
forum: General Help
---

### Post by lezz on 2006-04-22
1.
så här ser det ut i min /etc/dhcpd.conf. jag måste ha med alla dessa tre rader då jag har 3 NICs. de två första är för lanet här hemma och den sista för telia adsl modemet. egentligen vill jag bara dela ut ip till datorn som är kopplad till eth1 men om jag inte har med de andra två raderna (eth0,eth2) så klagar dhcpd servern vid uppstart att jag inte deklarerat subnäten för eth0 och eth2. hur fixar man detta? vill bara ha dhcp-servern aktiv på eth1!

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.254 192.168.0.254;
next-server 192.168.1.2;
filename "pxelinux.0";
}

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.254 192.168.1.254;
next-server 192.168.1.2;
filename "pxelinux.0";
}

subnet 213.67.187.0 netmask 255.255.255.0 {
range 213.67.187.254 213.67.187.254;
next-server 192.168.1.2;
filename "pxelinux.0";
}


2.
jag installerade tftpd med apt-get install tftpd men hur startar jag den automatiskt? det står använd inetd.conf men jag vet inte hur jag ska skriva där.

---

### Post by adamkane on 2006-04-22
Try english, german or french. Not swedish.

You want to know how to start tftpd automatically with 3 NICs?

---

