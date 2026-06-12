---
title: "Terminal stuck at busybox"
date: 2010-01-06
forum: General Help
---

### Post by vbundi on 2010-01-06
I'm running an LTSP install via the Alternate CD for 8.04.3.

I've got two DHCP servers on my network, and I've set the LTSP one as authoritative, and to only offer ip addresses to known (listed) hosts.

Terminal boots up, grabs ip from correct server... loads the kernel, and then does a *second* dhcp request, but for some reason it is going to the other server, and grabbing a different ip now.  The MAC hasn't changed so I don't understand why it's doing this.
The second dhcp request is supposed to happen according to this page:
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

Here is my dhcpd.conf for my LTSP server.
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

# Main Network
subnet 192.168.1.0 netmask 255.255.255.0 {
	authoritative;
	deny client-updates;
	deny unknown-clients;
	range 192.168.1.20 192.168.1.25;
	option domain-name "example.com";
	option domain-name-servers 192.168.1.127;
	option broadcast-address 192.168.1.255;
	option routers 192.168.1.127;
	# get-lease-hostnames true;
	option subnet-mask 255.255.255.0;
	option root-path "/opt/ltsp/i386";
	if substring( option vendor-class-identifier , 0 , 9 ) = "PXEClient" {
		filename "/ltsp/i386/pxelinux.0";
		}
	else {
		filename "/ltsp/i386/nbi.img";
		}
	# NeoTerm1
	host neoterm1 {
		hardware ethernet aa:bb:cc:dd:ee:11;
		}
	}

Any solutions for this that do not involve disabling my second dhcp server?

---

