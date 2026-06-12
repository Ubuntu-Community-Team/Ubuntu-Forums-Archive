---
title: "NIS with NFS mounted homeareas and failed mounts."
date: 2011-09-05
forum: General Help
---

### Post by deej1976 on 2011-09-05
Hi,

I've searched for this and in the end I think I've got a solution (hack).

[B]The Setup:
==========[/B]

Network is looked after by /etc/network/interfaces

#ETH0
auto eth0
iface eth0 inet dhcp

purged network-manager, gnome-network-manger, etc...

nis, autofs and required packages installed.

/etc/auto.master entry:
/home yp:auto.home --timeout=60,-fstype=nfs4

default user account homearea moved to another location.

cat /etc/yp.conf entires:
domain *nisdomainname* server *slave-nis1*
domain *nisdomainname* server *slave-nis2*

[B]The Bug:
========[/B]

Once gdm has started nis account users are unable to login as homeareas do not mount. Alt+F1 log in as local default account and run service autofs restart, Alt+F7 now NIS accounts can login.

[B]The Reason:
===========[/B]

Once the networking starts nis starts but does not complete until the network connections has completed, autofs comes up but without NIS it fails to setup the maps.

[B]The Solution:
=============[/B]

Two part solution, part one you need to modify grub to boot in text mode so that gdm does not start. This is done by modifying /etc/default/grub so that the line starting with GRUB_CMDLINE_LINUX= looks like:

GRUB_CMDLINE_LINUX="text"

run 'update-grub'

The second part requires setting up the script /etc/init.d/autofs-fix:

#!/bin/bash

ping -c 1 -W 60 *IP_ADDRESS* > /dev/null
until [ $? -eq 0 ]; do
	ping -c 1 -W 60 *IP_ADDRESS* > /dev/null
done

YPWHICH="blank"
until [[ $YPWHICH = "*nisdomainname*" ]]; do
	service nis restart
	YPWHICH=`ypdomainname`
done

service autofs restart
service gdm start

exit 0

i) Replace IP_ADDRESS with an know IP_ADDRESS on your network e.g. DNS server IP.
ii) Replace nisdomainname with your NIS domain name.

Now place a link to this in /etc/rc2.d e.g.

cd /etc/rc2.d
ln -s /etc/init.d/autofs-fix S99autofs-fix

Now when you reboot gdm will not start until nis has completed and autofs has been restarted.

---

