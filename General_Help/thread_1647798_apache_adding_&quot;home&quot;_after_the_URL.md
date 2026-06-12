---
title: "apache adding &quot;home&quot; after the URL"
date: 2010-12-17
forum: General Help
---

### Post by ialvik on 2010-12-17
Hi! 

I've installed apache on my ubuntu 10.10 to act as a proxy forward for Sickbeard. How ever Apache automagical changes the url from <url>/sickbeard to <url>/sickbeardhome every time. Any suggestions for config files I might have overlooked? (sabnzbd works like a charm though).

/etc/apache/http.conf

```
<Location /sabnzbd>
order deny,allow
deny from all
allow from all
ProxyPass http://<url>:8080/sabnzbd
ProxyPassReverse http://<url>:8080/sabnzbd
</Location>
<url>
<Location /sickbeard2>
order deny,allow
deny from all
allow from all
ProxyPass http://<url>:8081/sickbeard/
ProxyPassReverse http://<url>:8081/sickbeard/
</Location>

```

Config.ini (sickbeard)

```

[General]
log_dir = Logs
web_port = 8081
web_host = 10.0.0.1
web_ipv6 = False
web_log = 0
web_root = /sickbeard
web_username = ""
web_password = ""

```

---

