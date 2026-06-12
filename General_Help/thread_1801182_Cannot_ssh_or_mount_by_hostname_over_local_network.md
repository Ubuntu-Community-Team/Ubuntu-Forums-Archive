---
title: "Cannot ssh or mount by hostname over local network"
date: 2011-07-10
forum: General Help
---

### Post by dwasifar on 2011-07-10
I have several machines on a local network.  To save time and aggravation, I have a caching DNS server (using dnsmasq) on one machine, so I don't have to maintain hosts files on every machine.

On all my machines but one, this works fine to ssh in to other machines on the network, or to mount a share in fstab.  So, for example:

ssh dwasifar@gertrude (works from the command line)
gertrude:/storage/video /home/dwasifar/video nfs (works in /etc/fstab)

The exception is the one machine running Kubuntu 11.04.  On this machine, the hostnames do NOT work this way, and I either have to specify them in /etc/hosts, or use the IP instead of the hostname.

The Kubuntu box IS in fact hitting the local DNS.  Output from *host -v gertrude* is not fundamentally different from *host -v somedomain.com*.  Both return A records containing the appropriate IP.  But *ssh [email]dwasifar@somedomain.com[/email]* works (if there's an ssh server there) whereas *ssh dwasifar@gertrude* does not.

---

### Post by papibe on 2011-07-13
Could you post your /etc/nsswitch.conf ?  also, could you post the errors you get while using the short names?

Regards.

---

### Post by dwasifar on 2011-07-17
ssh error is:

ssh: Could not resolve hostname gertrude: Name or service not known.


Here is nsswitch.conf.  (It's identical to the same file on other machines without this problem.)

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by papibe on 2011-07-17
It looks ok.

The only thing I can think of is that you make sure they all are using the same dns server by checking this file:
```
/etc/resolv.conf
```
Something similar happened to me when I change one of my machines to use OpenDNS. It resolved addresses faster, but it stopped recognizing all local machines names. One simple solution is to use the zeroconf/avahi type of address:
```
gertrude.local
```
Just some thoughts,
Regards.

---

### Post by dwasifar on 2011-07-17
I solved it.  papibe put me on the right track.

On the Gnome machines, Network Manager lets you edit the auto eth0 connection.  I had those set to Automatic (DHCP) Addresses only.  This lets you add your own DNS, Domain, and Gateway entries.  I had DNS pointed at my local network's DNS server and the other two fields blank.  The resulting /etc/resolv.conf file contained only nameserver information.

On the KDE box, the Network Manager settings tool does not let you edit auto eth0.  So I had added the DNS server settings in /etc/dhcp3/dhclient.conf instead, so host queries would hit it.  However, this meant entries for domain and gateway were still appearing in resolv.conf, and pointing to my AT&T U-verse gateway.  Host queries were hitting that first.  The U-verse gateway doesn't know about the local DNS server, so it returned no results for local hostnames, and this was what was causing ssh and fstab to fail.  I realized this after papibe pointed me at /etc/nsswitch.conf.

You can't just edit resolv.conf, because it gets refreshed with every reboot.  So the solution was to add this to /etc/dhcp3/dhclient.conf:

```
supersede domain-name "";
```

This causes resolv.conf to be refreshed without the domain and gateway entries.  ssh and fstab now obtain IPs for local machines properly.

---

