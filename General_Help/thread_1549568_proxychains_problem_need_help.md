---
title: "proxychains problem need help"
date: 2010-08-09
forum: General Help
---

### Post by zerobinary on 2010-08-09
```
root@ubuntu:~# proxychains chromium-browser bing.com
ProxyChains-3.1 (http://proxychains.sf.net)
|DNS-request| clients2.google.com 
|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-|DNS-request| www.google.com 
|S-chain|-<>-213.0.88.86:8080-<><>-4.2.2.2:53-<>-91.205.174.48:80-<--denied
|DNS-response|: clients2.google.com is not exist
<><>-4.2.2.2:53-|DNS-request| clients2.google.com 
|S-chain|-<>-213.0.88.86:8080-|DNS-request| bing.com 
|S-chain|-<>-213.0.88.86:8080-<--denied
|DNS-response|: www.google.com is not exist
|DNS-request| www.google.com 
|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-<>-91.205.174.48:80-<>-91.205.174.48:80-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<--denied
|DNS-response|: clients2.google.com is not exist
<--denied
|DNS-response|: bing.com is not exist
|DNS-request| bing.com 
<--denied
|DNS-response|: www.google.com is not exist
|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-<><>-4.2.2.2:53-<--denied
|DNS-response|: bing.com is not exist
|DNS-request| linkhelp.clients.google.com 
|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-<><>-4.2.2.2:53-<--denied
|DNS-response|: linkhelp.clients.google.com is not exist
|DNS-request| linkhelp.clients.google.com 
|S-chain|-<>-213.0.88.86:8080-|DNS-request| www.google.com 
|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-<>-91.205.174.48:80-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<--denied
|DNS-response|: linkhelp.clients.google.com is not exist
<--denied
|DNS-response|: www.google.com is not exist
|DNS-request| www.google.com 
|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-<><>-4.2.2.2:53-|DNS-request| ymxphzbcey 
|DNS-request| npnecodrsl 
|DNS-request| ypnsautxvz 
|S-chain|-<>-213.0.88.86:8080-|S-chain|-<>-213.0.88.86:8080-|S-chain|-<>-213.0.88.86:8080-<--denied
|DNS-response|: www.google.com is not exist
<>-91.205.174.48:80-<>-91.205.174.48:80-<>-91.205.174.48:80-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<--denied
|DNS-response|: npnecodrsl is not exist
|DNS-request| npnecodrsl 
<--denied
|DNS-response|: ypnsautxvz is not exist
<--denied
|DNS-response|: ymxphzbcey is not exist
|DNS-request| ypnsautxvz 
|DNS-request| ymxphzbcey 
|S-chain|-<>-213.0.88.86:8080-|S-chain|-<>-213.0.88.86:8080-|S-chain|-<>-213.0.88.86:8080-<>-91.205.174.48:80-<>-91.205.174.48:80-<>-91.205.174.48:80-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<><>-4.2.2.2:53-<--denied
|DNS-response|: ymxphzbcey is not exist
<--denied
|DNS-response|: ypnsautxvz is not exist
<--denied
|DNS-response|: npnecodrsl is not exist
root@ubuntu:~# 

```
here is my configure file
```
[ProxyList]
# add proxy here
# meanwile
# defaults set to "tor"
http 	213.0.88.86 8080
http 	91.205.174.48 80

```
I have even try proxychains with my firefox!

---

### Post by Stoneface on 2010-08-10
Did you ever solve this problem? How?

---

### Post by zerobinary on 2010-08-13
No I have not solve the issues, but according to some ppl the only way to resolve it is to port forward it. The problem is I am not sure how to port forward it!

---

