---
title: "How to hide my proxy from whatismyip.com"
date: 2010-05-09
forum: General Help
---

### Post by karthick87 on 2010-05-09
Whenever i visit [www.whatismyip.com](www.whatismyip.com) it shows my ip address also it shows that i am using squid proxy..How to hide my proxy from these websites..?

---

### Post by peculiar penguin on 2010-05-09
I think Squid adds some HTTP headers (e.g. [http://en.wikipedia.org/wiki/X-Forwarded-For](http://en.wikipedia.org/wiki/X-Forwarded-For)), you'd have to check the docs to see if this can be turned off.

---

### Post by karthick87 on 2010-05-17
I am using squid v2.7 and there is no such option.

```
karthick@Learners-desktop:~$ squid -v
Squid Cache: Version 2.7.STABLE3

```

---

### Post by sedawk on 2010-05-17
Squid is a proxy with cache, so it is useful to reduce
network traffic when it connects a large network to the web.

If you are the only person using it think about using
something like privoxy.
It is a proxy for privacy and doesn't do the caching.

---

### Post by Soul-Sing on 2010-05-17
when i use ixquick as searchengine via SSL [COLOR="Red"]and proxy [/COLOR]it hides my ip adres perfectly at whatsmyip.com

---

### Post by karthick87 on 2010-06-25
I have done this by Uncommenting these lines in my squid configuration file..

```
request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access WWW-Authenticate allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access All deny all
```

---

