---
title: "confusing samba"
date: 2006-05-17
forum: General Help
---

### Post by hartunnoo on 2006-05-17
I setup a small network in my school and installed:

1. Web Server: Apache 2.0.x 
2. Mail Server: Postfix 
3. DNS Server: BIND9 
4. FTP Server: proftpd 
5. POP3/POP3s/IMAP/IMAPs:
6. Webalizer
7. Samba

The problem:

1. I add new student account into samba domain and then they can access their file locally. But the student cannot log on using ssh or ftp from their home place to access server in the school.

do this samba have different user account than normal user when we do the 1st time installation?

thank you.

---

### Post by Soarer on 2006-06-17
Its been a while, so maybe you fixed it by now...

Anyway, one thing missing from your list is a firewall. AFAIK Unbuntu blocks all incoming ports by default, so you have to open them somehow to allow access from outside. Those as know use iptables & stuff, but the rest of us will need a firewall,which is usually a GUI for iptables anyway. Try installing Firestarter or Shorewall (which I use) and open up some ports for the students. If you have a router you might need to look at its firewall too.

---

