---
title: "CIFS Mounts Only From IP Address, Not Server Name"
date: 2011-09-17
forum: General Help
---

### Post by kuloch on 2011-09-17
I'm trying to set up autofs but seem to be having a problem with name resolution.  The problem exists with a single mount.cifs command, so I can isolate it to this for simplicity.  The man page for mount.cifs says that a computer's name or IP address can be used in its service path, but it only works for me using the IP address.

This works fine.

```
mount.cifs //192.168.0.102/linuxbackup cifs/linuxbackup -o credentials=/path/to/smbcredentials
```

This pauses for a while before yielding the following error.

```
mount.cifs //office/linuxbackup cifs/linuxbackup -o credentials=/path/to/smbcredentials

mount error(110): Connection timed out
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I can see the share from Go => Network in Nautilus, and copying its path shows that it's using smb://office/linuxbackup.  It's obviously using a Samba client.  So I gave a shot at:

```
mount.smbfs smb://office/linuxbackup/ cifs/linuxbackup -o credentials=/path/to/smbcredentials

Mounting cifs URL not implemented yet. Attempt to mount smb://office/linuxbackup
No ip address specified and hostname not found
```

Any suggestions?  It looks to me like the name resolution is working (from Nautilus, at least), but not in the way I'm trying to use it.  It would be nice to use the Windows (XP) computer's name rather than IP address.

This is on Ubuntu 10.04.

---

### Post by papibe on 2011-09-17
Could you post the results of these commands?
```
$ nslookup office

$ dig office
```

Also could you post the content of these files:
```
/etc/resolv.conf
/etc/nsswitch.conf

```
Regards.

---

### Post by kuloch on 2011-09-17
```
**$ nslookup office**
Server:		209.18.47.61
Address:	209.18.47.61#53

Non-authoritative answer:
Name:	office
Address: 204.232.137.207
```

```
**$ dig office**

; <<>> DiG 9.7.0-P1 <<>> office
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52234
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;office.				IN	A

;; ANSWER SECTION:
office.			10	IN	A	204.232.137.207

;; Query time: 27 msec
;; SERVER: 209.18.47.61#53(209.18.47.61)
;; WHEN: Sat Sep 17 19:25:46 2011
;; MSG SIZE  rcvd: 40
```

Yeah, something's definitely looking not right there.  The local network is on 192.168.0 with a netmask of 255.255.255.0.  Even my external IP address is entirely different (174.101.237.81, currently).  It might be worth adding that "ping office" goes to 204.232.137.207 (100% loss) - the same as nslookup gives for the non-authoritative address.

Here are the two requested files' contents:

```
**$ cat /etc/resolv.conf**
nameserver 209.18.47.61
```

```
**$ cat /etc/nsswitch.conf**
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

I tried changing resolv.conf to "nameserver 192.168.0.1" (the router/gateway), but that only served to change the commands' server address for "office" to that IP address instead of the one above.

---

### Post by papibe on 2011-09-17
Somehow your machine is set to use an external DNS (probably from your ISP) instead of your router. Maybe because some routers don't have the capability to relay the DNS requests and just take themselves out of the equation.

The problem with that configuration is that the machines in your network won't know each other, unless they use some sort of independent broadcast system. 

Between Ubuntu machines you may use the .local trick because they use the avahi service ([zero configuration networking]("http://en.wikipedia.org/wiki/Zero_configuration_networking")).

Windows machine use NETBIOS services.

The first place I would look for a different configuration would be in your router. Maybe there's an option to set it to relay or masq the DNS service. If you can do that, just restart your machine a check if the file resolv.conf has a local address.

Another fix would be to install a netbios service and modify your rules in the nsswitch.conf accordingly. Here's a simple [tutorial]("http://ubuntuforums.org/showthread.php?t=88206") on how to accomplish that.

I hope it helps,
Regards.

---

### Post by dcstar on 2011-09-18
> **kuloch said:**
> 
.........
Any suggestions?  It looks to me like the name resolution is working (from Nautilus, at least), but not in the way I'm trying to use it.  It would be nice to use the Windows (XP) computer's name rather than IP address.

This is on Ubuntu 10.04.

You could simply add an entry into your **/etc/hosts** file.

---

### Post by kuloch on 2011-09-26
Aha, thank you for linking to that tutorial.  I had a while ago installed winbind and added "wins" to the nsswitch.conf, but I wondered why that didn't seem to do anything (and forgot all about it in the weeks before getting around to posting on here).

That tutorial points out that "order does matter" for the hosts line.  I had tacked "wins" onto the end, so presumably the DNS server was being asked first.  All is good, now.

---

### Post by papibe on 2011-09-26
:D Glad is working! Please mark the thread solved when you have the chance.

Regards.

---

