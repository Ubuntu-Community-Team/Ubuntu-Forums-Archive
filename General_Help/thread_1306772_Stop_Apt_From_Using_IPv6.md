---
title: "Stop Apt From Using IPv6"
date: 2009-10-30
forum: General Help
---

### Post by Pandora on 2009-10-30
I'm using Ubuntu 9.10 karmic. I have a working ipv6 tunnel, and I use it periodically. Problem is apt defaults to using it because ubuntu provides this functionality with their repositories. I can appreciate the ipv6 support from the Ubuntu team however this is not optimal for those of us going through a tunnel broker to get ipv6 support.  I do not wish to disable ipv6 completely, all I want is to force apt to use ipv4 instead. Is there any way I can do this?

---

### Post by lavinog on 2009-10-30
I have no experience with ipv6 yet, but does adding a manual ipv4 entry to /etc/hosts allow it to resolve to the ipv4 address instead?

---

### Post by Pandora on 2009-10-30
> **lavinog said:**
> I have no experience with ipv6 yet, but does adding a manual ipv4 entry to /etc/hosts allow it to resolve to the ipv4 address instead?

That's actually somewhat of a good temp fix. Thank you for taking the time to respond. 


I used dig to retrieve the relevant ipv4 information.

aaron@aaron-desktop:~$ **dig us.archive.ubuntu.com**

; <<>> DiG 9.6.1-P1 <<>> us.archive.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28530
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;**us.archive.ubuntu.com**.		IN	A

;; ANSWER SECTION:
us.archive.ubuntu.com.	96	IN	CNAME	ubuntu-archive.acc.umu.se.
ubuntu-archive.acc.umu.se. 96	IN	A	**130.239.18.173**
ubuntu-archive.acc.umu.se. 96	IN	A	**130.239.18.165**

;; Query time: 1 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Fri Oct 30 20:09:56 2009
;; MSG SIZE  rcvd: 110

I then added this information to my hosts file following the format the file is already in. 

I would not label this solved though because that domain will resolve to the specified ipv4 addresses system wide. God forbid ipv4 addresses need re-assigned and the ubuntu repos get a different one. Then I'm back to where I started. Ideally I want just for apt to specifically use ipv4 over ipv6.

---

### Post by Pandora on 2009-10-31
I've done some comprehensive googling and it looks like there is no way you can stop apt from looking in AAAA rather than A. I've currently disabled ipv6 all together in karmic by adding ipv6.disable=1 to the GRUB_CMDLINE_LINUX_DEFAULT string in /etc/default/grub

Ipv6 is not moduralized in karmic so passing a parameter during boot to the kernel is the only way I know how to disable it globally. This is actually really bad though, as I want to use ipv6 capabilities, I just don't want apt to download everything through my tunnel.

---

### Post by lavinog on 2009-10-31
> **Pandora said:**
> 
I would not label this solved though because that domain will resolve to the specified ipv4 addresses system wide. God forbid ipv4 addresses need re-assigned and the ubuntu repos get a different one. Then I'm back to where I started. Ideally I want just for apt to specifically use ipv4 over ipv6.
There should be a way write a script that keeps the entries updated.

---

