---
title: "I cannot change my DNS servers no matter what I do."
date: 2011-01-16
forum: General Help
---

### Post by anonSam on 2011-01-16
I changed my MAC address in /etc/network/interfaces. To make it work I had to change eth0 to eth1. The Internet connection works fine but network-admin is now gone. The icon is gone and the command line says: The program 'network-admin' is currently not installed. You can install it by typing: sudo apt-get install gnome-network-admin.

I've tried changing the DNS servers by hand in /etc/resolv.conf three different ways:

sudo gedit /etc/resolv.conf

gksudo "gnome-open %u"

gksudo nautilus

But every time I restart it resets back to my ISPs DNS servers. I'm afraid if I try to install network-admin again it's going to really mess everything up (just a feeling).

Any advice? I'm using Ubuntu 10.04.1. Also this may be related but I don't know: [http://ubuntuforums.org/showthread.php?t=974190](http://ubuntuforums.org/showthread.php?t=974190)

---

### Post by war59312 on 2011-02-08
As you found out, /etc/resolv.conf gets overridden on boot up.

You need to be using /etc/dhcp3/dhclient.conf instead.

1.) Run In Terminal:

> gksudo gedit /etc/dhcp3/dhclient.conf2.) Change Line 20 To:

> prepend domain-name-servers 208.67.220.220,208.67.222.222;Those IP address are for OpenDNS, simply change to different address if you wish to use something else.

3.) Then disconnect from network and reconnect.

---

