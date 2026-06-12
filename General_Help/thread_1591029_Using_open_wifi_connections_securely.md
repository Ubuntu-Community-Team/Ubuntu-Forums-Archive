---
title: "Using open wifi connections securely"
date: 2010-10-08
forum: General Help
---

### Post by t0p on 2010-10-08
I know about using vpns, and https sites, but that's not always an option; and what other (especially Ubuntu/Linux-specific) steps should I take when using someone else's open wifi connection to browse the web?

---

### Post by bodhi.zazen on 2010-10-08
Depends on what you are worried about.

1. VPN. Use ssh if you must :

[Proxy Firefox through a SSH tunnel "how to" @ Calomel.org - Open Source Research and Reference]("https://calomel.org/firefox_ssh_proxy.html") 

2. Enable your firewall

```
sudo ufw enable
```

3. Use apparmor for all network aware applications (firefox, weather applet, etc).

4. Stop , remove, or disable avahi .

5. Use a proxy server (privoxy).

---

