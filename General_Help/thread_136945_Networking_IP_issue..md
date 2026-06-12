---
title: "Networking IP issue."
date: 2006-02-27
forum: General Help
---

### Post by Tritis on 2006-02-27
My ip address is being changed by Kubuntu to 169.254.55.156.  If i choose DHCP or Manual I get this issue.  I have a 192.168.*.* IP for a few seconds and then it reverts to the 169 address.  The odd thing is that my network still seems to work fine.  ifconfig shows the 169 address as well as Network settings (which is where I'm making all the config changes.)

The file /etc/network/interfaces has the proper information, either iface eth0 inet dhcp for when I configure via dhcp or the 192 address that I entered into Network settings, yet ifconfig will still show the 169.  I do have VMWare installed since this morning and I haven't noticed this problem until later today.  Does anyone else notice a similar issue?  Or if VMware is not involved, how to resolve whatever is causing the strange IP?

---

### Post by jamesr on 2006-02-27
I believe that address 169.254.55.156 is part of a subnet reserved for automatic IP addressing - meaning, you get that address if either
1) you haven't statically assigned one or 
2) no dhcp server is available to give you one. Obviously you've assigned one, but the NIC isn't taking it.

Post a copy of the output from the command
sudo dhclient

---

