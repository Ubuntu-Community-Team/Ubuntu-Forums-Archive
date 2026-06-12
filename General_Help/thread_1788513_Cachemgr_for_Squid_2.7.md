---
title: "Cachemgr for Squid 2.7"
date: 2011-06-22
forum: General Help
---

### Post by fforoge on 2011-06-22
Hi folks,
I have set up a Squid 2.7 within a Ubuntu 10.04 environment, but have become stuck in setting up the Web based monitoring going.

I have been using the following reference material 
[IMG]http://my.safaribooksonline.com/static/201106-2138-oreilly/images/9781849513906/9781849513906_s.jpg[/IMG]
[LIST]
[*]**Squid Proxy Server 3.1**
[/LIST]
but have found a flaw in the required script for Apache2 for cachemgr (see below). My understanding is Cachemgr is part of Squid 2.7. However in the below recommended script the path /opt/squid/libexec/cachemgr.cgi did not exist! 

Ok so I created it, did a search for cachemgr.cgi, and moved it across. However Apache2 spat it out (internal configuration error) and I do not have enough skills to know how to fix it.

Can anyone point me to a fix, or provide a HOWTO to get Cachemgr working for squid.

Thanks in advance.

ScriptAlias /Squid/cgi-bin/cachemgr.cgi /opt/squid/libexec/cachemgr.cgi
# Only allow access from localhost by default
<Location /Squid/cgi-bin/cachemgr.cgi>
order allow,deny
allow from localhost
# If we want to allow access to cache manager from 192.0.2.25,
# uncomment the following line
# allow from 192.0.2.25
# Add additional allowed hosts as needed
# allow from .example.com
</Location>

---

