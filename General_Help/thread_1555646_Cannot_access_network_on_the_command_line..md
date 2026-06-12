---
title: "Cannot access network on the command line."
date: 2010-08-18
forum: General Help
---

### Post by glimmung on 2010-08-18
Hi All,

I am having a strange problem with Ubuntu 10.04 that I will be much grateful if resolved.

I cannot connect to the internet on the command line. Things like firefox or chrome browser work fine. But on the command line programs like 'links' fail to work. This is on a machine behind a proxy, I have the http_proxy and https_proxy environment variables set properly. Any help into how to go about diagnosing and resolving this will be appreciated. I can access the localhost URLs through the command line if that is any help.

---

### Post by DaithiF on 2010-08-18
is the proxy an actual proxy address (host:port), or does it point to a '.pac' file (which contains a piece of javascript that browsers can execute and which resolves to a particular proxy address).  command line tools usually can't handle this, so you need to (manually) look through the logic in the .pac file and tell them an actual proxy address to use.

---

### Post by glimmung on 2010-08-19
> **DaithiF said:**
> is the proxy an actual proxy address (host:port), or does it point to a '.pac' file (which contains a piece of javascript that browsers can execute and which resolves to a particular proxy address).  command line tools usually can't handle this, so you need to (manually) look through the logic in the .pac file and tell them an actual proxy address to use.

This is an actual proxy address. Supplied using 
```
export http_proxy="http://192.168.1.50:3128"
```

The same proxy is used in the network settings which is picked up fine by Firefox. 

Also, if it helps, DNS resolution does not happen on the command line. If I give 'ping [www.google.com](www.google.com)' or 'host [www.google.com](www.google.com)' it will not resolve the IP unless it is in the /etc/hosts file. One side effect of this is that apt-get did not work until I put the Ubuntu servers in the host file, but Synaptic package manager from the administration menu worked fine.

---

### Post by DaithiF on 2010-08-19
try curl passing in an explicit proxy address, and see how it gets on:
```
curl --proxy http://192.168.1.50:3128 -v http://www.google.com

```

---

### Post by glimmung on 2010-08-20
> **DaithiF said:**
> try curl passing in an explicit proxy address, and see how it gets on:
```
curl --proxy http://192.168.1.50:3128 -v http://www.google.com

```

It does seem to connect in this case. This is what I get:


```
* About to connect() to proxy 192.168.1.50 port 3128 (#0)
*   Trying 192.168.1.50... connected
* Connected to 192.168.1.50 (192.168.1.50) port 3128 (#0)
> GET http://www.google.com HTTP/1.1
> User-Agent: curl/7.19.7 (x86_64-pc-linux-gnu) libcurl/7.19.7 OpenSSL/0.9.8k zlib/1.2.3.3 libidn/1.15
> Host: www.google.com
> Accept: */*
> Proxy-Connection: Keep-Alive
> 
< HTTP/1.1 302 Found
< Location: http://www.google.co.in/
< Cache-Control: private
< Content-Type: text/html; charset=UTF-8
< Date: Fri, 20 Aug 2010 07:35:31 GMT
< Server: gws
< Content-Length: 221
< X-XSS-Protection: 1; mode=block
< Set-Cookie: PREF=ID=78fad5427f3f33cc:TM=1282289731:LM=1282289731:S=xC46xhhH0O6UtjdF; expires=Sun, 19-Aug-2012 07:35:31 GMT; path=/; domain=.google.com
< Set-Cookie: NID=38=CQJC-3_vr50s5Z4OJcNlYWQZQfxysVIGarzC573cIvviLQOl-WHss2EBmtAosTDgDiTGKIbuRcFxFo9AVnjqsB4YYH6j_DtNrK7wcsCUtralfOTU-KEHtqXl8bD3mpjz; expires=Sat, 19-Feb-2011 07:35:31 GMT; path=/; domain=.google.com; HttpOnly
< Proxy-Connection: Keep-Alive
< 
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>302 Moved</TITLE></HEAD><BODY>
<H1>302 Moved</H1>
The document has moved
<A HREF="http://www.google.co.in/">here</A>.
</BODY></HTML>
* Connection #0 to host 192.168.1.50 left intact
* Closing connection #0
```

---

### Post by glimmung on 2010-08-20
Thanks for your help. I think I may have some more pointers. It may be because I have DHCP, but the DHCP server does not provide DNS settings.

---

