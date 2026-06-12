---
title: "Using Ubuntu with MS-Windows DHCP/DNS Servers"
date: 2006-04-04
forum: General Help
---

### Post by parker13 on 2006-04-04
My company insists on using MS Windows-based DHCP and DNS servers on our site LAN. I added an Ubuntu box to this network, which got its IP address over DHCP without any problems, but was never automatically added to the DNS server. Therefore, I always had to refer to the machine by its IP address and not its hostname, which was a real pain, as the IP address changed every time it was rebooted.

This bothered me because it worked for XP PCs, Macs and even old Debian Linux boxes.

After some trial and error, I discovered that it works if add the hostname to the file /etc/dhcp3/dhclient.conf, e.g:

send host-name "hetfield.acme.com";

...the DNS server is updated and I can ping hetfield from any box.


While this solves the problem, does anybody know why adding a "hostname" entry to /etc/network/interfaces didn't do the trick? I tried the following with no luck:

iface eth0 inet dhcp
  hostname hetfield.acme.com

Garry.

---

