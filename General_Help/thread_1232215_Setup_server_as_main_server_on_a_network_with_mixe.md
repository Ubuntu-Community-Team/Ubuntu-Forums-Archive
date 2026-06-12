---
title: "Setup server as main server on a network with mixed workstations"
date: 2009-08-05
forum: General Help
---

### Post by bazianm on 2009-08-05
Hi,

I am fairly new to Ubuntu Server. I do mostly windows. I have used Ubuntu servers as database and web servers and that's pretty much it.

I have a situation whereby a client (a school) would like to setup an ubuntu server with the server as the equivalent of a windows domain controller. Students and staff would log into the server. The server should be the security hub (like windows Active Directory). Each user would have their own space on the network server for storage. Security should be managed locally.

We will have Windows XP machines, Linux machines (flavor undetermined yet although I would recommend that they use Ubuntu for obvious reasons) and Macs.

1) Can Ubuntu Server handle this?
2) If I could be pointed in the right direction in terms of how to do this, I would appreciate it (assuming #1 is a yes).

Thanks

---

### Post by Iowan on 2009-08-05
[Here]("https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)") is an article about an LDAP server... but somewhat dated.
[This]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html") one is somewhat more current.
And a [perfect server]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2") article from howtoforge.com

---

