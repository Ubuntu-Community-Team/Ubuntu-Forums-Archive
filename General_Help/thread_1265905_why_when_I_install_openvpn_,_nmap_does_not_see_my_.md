---
title: "why when I install openvpn , nmap does not see my running ssh daemon?"
date: 2009-09-14
forum: General Help
---

### Post by frenchn00b on 2009-09-14
why when I install openvpn , nmap does not see my running ssh daemon?

I can see it
nmap IP
111/tcp
443/tcp open...

when I install openvpn, its finished this ssh is not visible anymore, when I do again this nmap command from root?

with -sS same result.

---

### Post by bchurchill on 2009-09-14
double check that your openvpn server is actually running (it probably isn't), that firewalls are setup appropriately and that you've nmaped the right IP address.

On the host computer, try

$netstat -a | grep LISTEN

and see if the ssh/vpn service is listed (you can also grep for the port number, if you know it.  It could be 22, but i'm not sure).  If it's not listed, try restarting your openvpn server:

$/etc/init.d/something-or-other start

---

### Post by bchurchill on 2009-09-14
also, speaking of port numbers, it could be that SSH is running on a non-standard port and NMAP isn't looking for it, since nmap only checks 1000 common ports by default.  If you have a low-latency connection,  or more time you could try

nmap -p1-65535 servers-ip

to see if this is the case.

---

