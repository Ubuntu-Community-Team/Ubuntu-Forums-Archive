---
title: "Strange network behavior with MSI 770-G45 &amp; Atheros AR8131"
date: 2010-09-19
forum: General Help
---

### Post by sdevine01 on 2010-09-19
Hey everyone,

I'm not sure if there is a bug here, or if its just user error, but I'll post the info in hopes that it might help someone else.

I recently did a Motherboard/CPU swap on a Lucid system and I noticed a problem when trying to retrieve some files from the apache server - "garbage" data was appearing before the HTTP response headers:

GET /%7Esdevine/lines.txt HTTP/1.1
Host: 10.0.0.3
Connection: Keep-Alive, TE
TE: trailers, deflate, gzip, compress
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)
If-Modified-Since: Thu, 01 Jan 1970 00:00:00 GMT
Accept-Encoding: deflate, gzip, x-gzip, compress, x-compress


[B].$....@a......E..D.R@.@...
...
..3.P...9....RrP..l.[/B]<..HTTP/1.1 200 OK
Date: Sun, 19 Sep 2010 13:59:54 GMT
Server: Apache/2.2.14 (Ubuntu)
Last-Modified: Sun, 19 Sep 2010 13:52:23 GMT
ETag: "bc0034-1fe9-4909d1aef53c0"
Accept-Ranges: bytes
Content-Length: 8169
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/plain


I ended up removing the "atl1c" module that Lucid loaded, and built an "atl1e" module from Atheros ([http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)) and that seemed to fix the problem.

---

