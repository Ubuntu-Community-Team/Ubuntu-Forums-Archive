---
title: "CLI command formation help reqd"
date: 2012-07-14
forum: General Help
---

### Post by Vishal Agarwal on 2012-07-14
Hi,

Pl advise how can I search the { "-" "-"} in apache/access.log in such type of below data:

180.76.6.35 - - [14/Jul/2012:08:34:16 +0600] "GET / HTTP/1.1" 200 1162 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)"
87.114.24.127 - - [14/Jul/2012:08:43:07 +0600] "-" 408 0 [COLOR=Navy]"-" "-"[/COLOR]
68.83.27.44 - - [14/Jul/2012:08:45:24 +0600] "-" 408 0[COLOR=Navy] "-" "-"[/COLOR]
119.63.196.30 - - [14/Jul/2012:08:52:05 +0600] "GET /dymq/cond-79.html HTTP/1.1" 404 471 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)"
72.42.166.140 - - [14/Jul/2012:08:53:01 +0600] "-" 408 0[COLOR=Navy] "-" "-"[/COLOR]
122.144.11.45 - - [14/Jul/2012:08:53:02 +0600] "OPTIONS / HTTP/1.0" 200 242 "-" "Microsoft-WebDAV-MiniRedir/5.1.2600"
122.144.11.45 - - [14/Jul/2012:08:53:02 +0600] "PROPFIND /homes HTTP/1.0" 405 581 "-" "Microsoft-WebDAV-MiniRedir/5.1.2600"
122.144.11.45 - - [14/Jul/2012:08:53:02 +0600] "PROPFIND /homes HTTP/1.0" 405 581 "-" "Microsoft-WebDAV-MiniRedir/5.1.2600"
122.144.11.45 - - [14/Jul/2012:08:53:02 +0600] "PROPFIND /Installation HTTP/1.0" 405 588 "-" "Microsoft-WebDAV-MiniRedir/5.1.2600"

---

### Post by diesch on 2012-07-14
```
grep '"-" "-"' apache/access.log
```

---

### Post by Vishal Agarwal on 2012-07-14
Thanks A lot.
Problem Solved

---

