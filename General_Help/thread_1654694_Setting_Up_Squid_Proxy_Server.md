---
title: "Setting Up Squid Proxy Server"
date: 2010-12-28
forum: General Help
---

### Post by HpZ on 2010-12-28
Hi, I followed this guide: 
[http://www.howtoforge.com/linux_secure_browsing_squid]("http://www.howtoforge.com/linux_secure_browsing_squid")
 and restart the Squid Server with no errors but when I try to SSH into it:
```
 ssh -L 8080:squidserver:8080 user@squidserver
```
It just hangs there for a long time, not timing out and eventually (after a long wait) I get this:
```
ssh_exchange_identification: Connection closed by remote host
```What could be the problem? I can SSH normally into the computer, but not into the proxy server. Do I need to forward the 8080 port on that network? I can't really access the router setup page from where I am.

---

### Post by dcstar on 2010-12-28
> **HpZ said:**
> Hi, I followed this guide: 
[http://www.howtoforge.com/linux_secure_browsing_squid]("http://www.howtoforge.com/linux_secure_browsing_squid")
 and restart the Squid Server with no errors but when I try to SSH into it:
```
 ssh -L 8080:squidserver:8080 user@squidserver -p 8080 
```
It just hangs there for a long time, not timing out and eventually (after a long wait) I get this:
```
ssh_exchange_identification: Connection closed by remote host
```What could be the problem? I can SSH normally into the computer, but not into the proxy server. Do I need to forward the 8080 port on that network? I can't really access the router setup page from where I am.

Why on earth are you trying to SSH into a web server port?

Web servers are for **browsers**.

---

### Post by HpZ on 2010-12-28
I'm just following the tutorial...

---

