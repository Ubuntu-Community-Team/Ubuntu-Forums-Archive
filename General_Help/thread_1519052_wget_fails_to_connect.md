---
title: "wget fails to connect"
date: 2010-06-27
forum: General Help
---

### Post by jackaloper on 2010-06-27
i have a problem with wget. It does not seem to consider the proxy parameter that i have put in /root/.bashrc and /etc/.wgetrc
In /root/.bashrc I added the lines: 
http_proxy=http://proxy.uwc.ac.za:3128/
export http_proxy
export no_proxy=$(echo $no_proxy | sed 's/,$//')

In  /etc/.wgetrc i added: 
https_proxy = [http://proxy.uwc.ac.za:3128/](http://proxy.uwc.ac.za:3128/)
http_proxy = [http://proxy.uwc.ac.za:3128/](http://proxy.uwc.ac.za:3128/)
ftp_proxy = [http://proxy.uwc.ac.za:3128/](http://proxy.uwc.ac.za:3128/)

I suspect there is something wrong because I save the files  /root/.bashrc and /etc/.wgetrc after editing I get :
error: line 53471: bad flag vector alias
error: line 53473: bad flag alias index: 0
error: line 53473: bad flag vector alias
error: line 53474: bad flag alias index: 0
error: line 53474: bad flag vector alias
error: line 53475: bad flag alias index: 0
error: line 53475: bad flag vector alias
error: line 53476: bad flag alias index: 0
error: line 53476: bad flag vector alias

When I do for example google like:
wget google.com

I get:

--2010-06-27 21:39:38--  [http://google.com/](http://google.com/)
Resolving google.com... 64.233.179.104
Connecting to google.com|64.233.179.104|:80... failed: Connection timed out.
Retrying.

--2010-06-27 21:40:00--  (try: 2)  [http://google.com/](http://google.com/)
Connecting to google.com|64.233.179.104|:80... 

Why cannot wget use the proxies that i set and authenticated in System -Preferences-Network Proxy?

---

