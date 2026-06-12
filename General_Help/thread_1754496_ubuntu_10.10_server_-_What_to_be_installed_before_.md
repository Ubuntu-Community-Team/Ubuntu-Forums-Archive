---
title: "ubuntu 10.10 server - What to be installed before installing my application software?"
date: 2011-05-10
forum: General Help
---

### Post by chuawenching on 2011-05-10
Hi everyone,

I am new to ubuntu, been a windows user. Found it fascinated with ubuntu.

My scenarios.

I have a Virtual Private Server with Ubuntu Server 64 bits 10.10 (i didn't know about 10.04 LTS till today, but if I need a re-format it will cost me money). I am setting up this server as a development & testing machine to setup wordpress, liferay and openerp. Now before I am go for software (which I roughly know how to install with apt-get), what should I do to make sure is right at the start, secure at least, etc.

My hosting provider already created me a master zone thing (outside of my VPS) so my domain [www.abc.com]("http://www.abc.com") (example) will point to the master zone nameservers.

I have only 1 IP Address, 1 vcpu, 160GB RAID hard disk and 1GB of ram (may increase no issue for me).

My plans are below:-
- setup a mail server
- setup sub domains - portal.abc.com (runs port 8085), erp.abc.com (runs port 8080) and wordpress (run ports 80) 
- setup the right security measures
- setup iptables (not sure needed for my scenarios) or apache2 reverse proxy???
- setup https for my portal and erp applications, security certificate, etc?
- install webmin
- and of course install my software via sudo apt-get... (software and databases too) - which i roughly know how (not main concern here)

Do I need to setup subnet or DNS within my VPS to allow above happen?

Is there any step by step tutorial out there to install for ubuntu 10.10 or similar to do almost similar to my plans above?

i notice most tutorials are separated, but i am worried I will miss out some security steps or something.

any help? Thanks in advance.

---

