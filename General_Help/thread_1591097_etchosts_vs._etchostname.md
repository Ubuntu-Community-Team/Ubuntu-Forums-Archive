---
title: "/etc/hosts vs. /etc/hostname"
date: 2010-10-08
forum: General Help
---

### Post by leesiulung on 2010-10-08
What is the difference between /etc/hosts and /etc/hostname?

I think the /etc/hosts file stores all ip address associated with this computer, but what about /etc/hostname? 

It sounds almost like the computer name, but what is it used for?

Help would be much appreciated for a beginner.

---

### Post by fragos on 2010-10-08
/etc/hostname is the where the hostname is set. It can be changed by editing the file. Normally /etc/hosts will reference the hostname as well as IP's.

---

### Post by leesiulung on 2010-10-08
But you can have multiple hostnames in the hosts file, but only one hostname in the hostname file?

---

### Post by fragos on 2010-10-08
> **leesiulung said:**
> But you can have multiple hostnames in the hosts file, but only one hostname in the hostname file?

Correct -- hostname sets your hostname, hosts relates hostnames to IP addresses.

---

### Post by leesiulung on 2010-10-08
So basically what is that hostname set in /etc/hostname used for in relation to

a) apache?

b) mail server?

Does it have any effect at all?

---

### Post by bab1 on 2010-10-08
> **leesiulung said:**
> So basically what is that hostname set in /etc/hostname used for in relation to

a) apache?

b) mail server?

Does it have any effect at all?

The hostname is the name the OS recognizes as its name.  At one time this was all you needed to identify one host from another.  For example I have 3 hosts in my LAN.  They are:[LIST]
[*]oak
[*]elm
[*]pine
[/LIST]

These are defined in the /etc/hostname file.  There are routines in Linux that refer to the name in the hostname file.

With TCP/IP you have an interface (NIC) that connects you to your local network.  It has an IP address.

You can communicate with these hosts using either the IP address or a more memorable alias.  The easiest would be to use the hostname.  This mapping of the alias originally was done with the /etc/hosts file.  A logical extension of  this is what is used with DNS.

Just as you can have nicknames for your friends (i.e Bob for Robert or Bill for William) you can do the same for the machines in your network.  You can have multiple entries in the /etc/hosts file.  See below for an example
```
192.168.1.10  elm woody
192.168.1.100  robert bob
```
Note that these names are referring to a mapping of IP a name.  You could ping the host "elm" with *ping elm *or you could ping the same host with the name "woody" as in *ping woody*.  They will both resolve to the same IP address (192.168.1.10).

This will work on a LAN but not in a WAN (internet) situation.  For that you would need a DNS name (FQDN (Fully Qualified Domain Name).  This usually a combination of the hostname and the domain name, as in *[COLOR="Green"]hostname.domainname.com[/COLOR]*.  If you had a domain such as *tree.com* you might have a FQDN like this *[COLOR="Blue"]elm.tree.com[/COLOR]*.  This  would be the *A name *record in DNS server and it would basically provide the the same IP to name mapping as a hosts file entry.  You can add aliases (i.e woody) using a *C name *record.

If you are running a web server (apache) or a mail server that is public facing you would need a DNS server to provide the IP to name mapping.  

I believe that you can use just the hostname mapping (no domain name)  If you are running these servers only on a LAN.

---

### Post by fragos on 2010-10-09
On your LAN you can use {hostname}.local instead of an IP address. For example my hostname is Geo and it can be addressed as Geo.local

---

