---
title: "How do I download a Hotmail folder: 'gotmail''?"
date: 2010-04-01
forum: General Help
---

### Post by bliffle on 2010-04-01
I'm trying to download an entire folder from my Hotmail account. I don't think there's any way to do it with just Hotmail. So I'm trying 'gotmail'. Here's my run (with security info starred out):

```
john@JHT60-250gb:~$ gotmail  --domain hotmail.com --password ******* --username john_******** --verbose --folders "SCC"  --folder-directory /home/john/SCC

Gotmail v0.9.0    Copyright (C) 2000-2003 Peter Hawkins
Gotmail comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.

CVS ident: $Id: gotmail.in 112 2006-07-17 13:05:43Z kartar $

Running at Thu Apr  1 12:35:39 2010 for user john_*******

System version is: linux
Perl version is:   5.010000
Curl version is:   curl 7.18.2 (i486-pc-linux-gnu) libcurl/7.18.2 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.10
Protocols: tftp ftp telnet dict ldap ldaps http file https ftps 
Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz 

Getting hotmail index page...
FETCH: http://www.hotmail.com/
Trying [1/2]...
Following redirect to http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=11&ct=1270150536&rver=6.0.5285.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&lc=1033&id=64855&mkt=en-US
FETCH: http://login.live.com/login.srf?wa=wsignin1.0&rpsnv=11&ct=1270150536&rver=6.0.5285.0&wp=MBI&wreply=http:%2F%2Fmail.live.com%2Fdefault.aspx&lc=1033&id=64855&mkt=en-US
Trying [1/2]...
Page doesn't contain any form action field!
john@JHT60-250gb:~$ 

```

Don't know what that means.

Is there a Firefox addon that will do it?

Can I send all the msgs to Thunderbird and does Thunderbird have a way to dump a folder into a directory?

---

