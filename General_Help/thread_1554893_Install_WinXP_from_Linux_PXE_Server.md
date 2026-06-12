---
title: "Install WinXP from Linux PXE Server?"
date: 2010-08-17
forum: General Help
---

### Post by gus_zernial on 2010-08-17
I need to install Windows XP on a Toshiba R100 laptop,
which has no CD or floppy drives, but which supports
PXE boot over a network. I have a Kubuntu 10.04 box, 
which I believe can be set up as a PXE server (tho I
have no experience doing so). Is it possible to install 
WinXP onto the Toshiba R100 as a client from my Kubuntu 
box as a PXE server? If so, a pointer to a HowTo or 
other instructions would be appreciated.

Thx, Gus

---

### Post by Ferb on 2010-08-23
I haven't worked with booting windows form a server but I believe the basics will still apply. I use dnsmasq as 'n dhcp server as well as booting tftp. You only have to add one/two lines to the dnsmasq.conf file and you will have a computer that will get an ip from the server and look to boot from a specific folder you specify. There is quite a few how-to's just google dnsmsaq pxe ubuntu. I can walk you through everything I know (it is not a lot) but it works for me. I maintain 110 pc's in three different labs.

---

