---
title: "lighttpd base_docroot doesn't exist"
date: 2009-09-12
forum: General Help
---

### Post by whiterook6 on 2009-09-12
Hi

I'm fairly new to linux, but I've got a spare computer lying around so I'm trying to set up a linux-lighty-mysql-php for a blog. Most of my knowledge of linux comes from friends telling me what to type.

Anyways, I think I've mucked something up. When I try to start lighttpd it gives me errors; first was

Duplicate config variable in conditional 0 global: fastcgi.server
2009-09-12 09:08:12: (configfile.c.855) source: /etc/lighttpd/mod_fastcgi.conf line: 9 pos: 1 parser failed somehow near here: (EOL)
2009-09-12 09:08:12: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 172 pos: 1 parser failed somehow near here: (EOL)

then

2009-09-12 09:17:52: (configfile.c.1136) base-docroot doesn't exist: /var/www/html
2009-09-12 09:17:52: (server.c.591) setting default values failed

and I've tried editing the /etc/lighttpd/lighttpd.conf and mod_fastcgi.conf to make it work, but it's only getting worse and worse. I tried removing and reinstalling lighttpd using aptitude but the error never goes away, and as a last ditch effort I deleted those two files and downloaded sample ones, but no luck.

I figure it's easier to remove the whole thing and start from scratch but I don't know how to do that. Can someone help? Thanks in advance!


Tim

---

