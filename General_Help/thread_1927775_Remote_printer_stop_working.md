---
title: "Remote printer stop working"
date: 2012-02-18
forum: General Help
---

### Post by K-Jtan on 2012-02-18
Hi everyone,

I have 3 computers at home, one that I use as a server, and two laptops for my girlfriend and I. A few weeks ago, I manage to make samba work and I was able to share my printer that was plug in my server (running ubuntu 11.10). My first laptop, running ubuntu 11.10, and my second laptop running Windows 7, were able to connect to it and print with no problem.

Today, we decided to put the printer at his right place (not on the floor plug in the front end USB like it use to be for the last few days ;) ). So I decided to plug the printer in the rear USB port and this is where thing started to go wrong. I can't print with my first laptop (running Ubuntu 11.10). But it's working with my 2nd laptop (running windows 7).

checked the samba configuration, reinstall the printer through CUPS web interface, reinstall the printer on my laptop... nothing works

this is what I have in my smb.conf file

```
[...]
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
[...]

```

Does anyone have an idea how to fix this

Thank you for your time

---

### Post by K-Jtan on 2012-05-03
I fixed this by using samba instead of Cups

---

