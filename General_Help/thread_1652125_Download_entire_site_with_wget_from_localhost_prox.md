---
title: "Download entire site with wget from localhost proxy"
date: 2010-12-24
forum: General Help
---

### Post by tah_206207 on 2010-12-24
hello i want to download android developer guide from google site but code.google is forbidden from my country i want to use wget to download entire android dev guides with freedom( proxy ) that i set in firefox these for open forbidden sites ( 127.0.0.1 port:8080 ) i use this command to download entire site 
```

`wget -U "Mozilla/5.0 (X11; U; Linux i686; nl; rv:1.7.3) Gecko/20040916" -r -l 2 -A jpg,jpeg -nc --limit-rate=20K -w 4 --random-wait http://developer.android.com/guide/index.html http_proxy http://127.0.0.1:8080 -S -o AndroidDevGuide`
```
but i can't download site and have this error
```

> --2010-12-24 17:05:29--  http://developer.android.com/guide/index.html
Resolving developer.android.com... 74.125.77.121, 2a00:1450:8001::79
Connecting to developer.android.com|74.125.77.121|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.0 403 Forbidden
  Date: Fri, 24 Dec 2010 13:35:28 GMT
  Content-Type: text/html
  Server: Google Frontend
  Content-Length: 1973
  Connection: Keep-Alive
2010-12-24 17:05:30 ERROR 403: Forbidden.

    
--2010-12-24 17:05:36--  http://http_proxy/
Resolving http_proxy... failed: Name or service not known.
wget: unable to resolve host address `http_proxy'
--2010-12-24 17:05:42--  http://127.0.0.1:8080/
Connecting to 127.0.0.1:8080... connected.
HTTP request sent, awaiting response... 
  HTTP/1.0 400 Bad Request
  Server: squid/2.7.STABLE9
  Date: Fri, 24 Dec 2010 13:35:40 GMT
  Content-Type: text/html
  Content-Length: 1488
  X-Squid-Error: ERR_INVALID_REQ 0
  X-Cache: MISS from ems08.your-freedom.de
  X-Cache-Lookup: NONE from ems08.your-freedom.de:3128
  Via: 1.0 ems08.your-freedom.de:3128 (squid/2.7.STABLE9)
  Connection: close
2010-12-24 17:05:42 ERROR 400: Bad Request
```

my freedom proxy is open when i want to download.

---

### Post by elliotbeken on 2010-12-24
IM me i might be able to help ..

---

### Post by tah_206207 on 2010-12-25
> **elliotbeken said:**
> IM me i might be able to help ..
I don't understand what's  your purpose?
can you help me to download site with wget from proxy?

---

### Post by efflandt on 2010-12-25
**man wget** does NOT show an **http_proxy** command line option, so wget is just interpreting "http_proxy" as another site to retrieve.  You either need to set a general proxy for your system from Network Proxy in the System menu at the top of your screen first (not sure if under Preferences or Administration, because I am in Natty without those menus), or before using wget, you first have to do something like:

```
export http_proxy='http://127.0.0.1:8080'
```But I don't see how that would help you unless that relays to another proxy outside of your country, because if your country blocks that site from your browser, it would also block it from a local proxy on your computer.  You would have to use a proxy outside of your country that you could get to (or tunnel to).

BTW when someone says to IM (instant message) them it means to click on their name in the left panel of their reply and click "Send a private message to ...".  Whenever they visit the forum next, a pop up would tell them that they have a message waiting.

---

### Post by tah_206207 on 2010-12-26
> **efflandt said:**
> **man wget** does NOT show an **http_proxy** command line option, so wget is just interpreting "http_proxy" as another site to retrieve.  You either need to set a general proxy for your system from Network Proxy in the System menu at the top of your screen first (not sure if under Preferences or Administration, because I am in Natty without those menus), or before using wget, you first have to do something like:

```
export http_proxy='http://127.0.0.1:8080'
```But I don't see how that would help you unless that relays to another proxy outside of your country, because if your country blocks that site from your browser, it would also block it from a local proxy on your computer.  You would have to use a proxy outside of your country that you could get to (or tunnel to).

BTW when someone says to IM (instant message) them it means to click on their name in the left panel of their reply and click "Send a private message to ...".  Whenever they visit the forum next, a pop up would tell them that they have a message waiting.
Yes this is ok
I thank you alot.
[Solved]

---

