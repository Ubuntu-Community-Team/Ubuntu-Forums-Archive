---
title: "Scripting help"
date: 2009-08-09
forum: General Help
---

### Post by Patricrawley on 2009-08-09
Is there a way to write a script that pulls my ip from whatismyip.com and sends it to me in an email every day? My isp doesn't allow static ips and I need to know my ip to tunnel into my ssh server. What can I do? I figure I would have to put the script into cron tab. But I don't know enough about writing scripts to do that part on my own.

---

### Post by Slim Odds on 2009-08-09
try dyndns

---

### Post by Patricrawley on 2009-08-09
Thanks, I didn't know about this. That really helps!

---

### Post by blueridgedog on 2009-08-09
> **Patricrawley said:**
> How can I use this to ssh in?

If you subscribe to some of the dynamic DNS hosting sites, then configure your router or Ubuntu system to update their site (using the instructions they provide) you will be able to get your home system with a url such as myhouse.dynamicdns.com.

---

### Post by nikhilbhardwaj on 2009-08-09
another one is no-ip.org

---

### Post by mdebusk on 2009-08-09
> **Patricrawley said:**
> Is there a way to write a script that pulls my ip from whatismyip.com and sends it to me in an email every day?

Redirect the following to whatever you use for automated mail:
```
lynx -dump http://www.whatismyip.com/automation/n09230945.asp
```

---

