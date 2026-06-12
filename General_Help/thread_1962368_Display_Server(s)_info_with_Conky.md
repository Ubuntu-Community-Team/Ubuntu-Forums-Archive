---
title: "Display Server(s) info with Conky ?"
date: 2012-04-21
forum: General Help
---

### Post by Mobidoy on 2012-04-21
Is it possible to get Conky to display info from distant servers ? 

mem usage, users logged in, cpu usage etc ?

---

### Post by Habitual on 2012-04-21
There are two methods that can be used:
Both shown here utilize ssh keys for password-less interactivity.

Method 1:
Retrieval of external data piped into a output file and conky can display that output file contents 
```
ssh user@domain.com uptime > ~/remotehost.uptime
```and process that with conky using
```
${execi 600 cat ~/remotehost.uptime}
```[B]
or...[/B]
Method2:
```
${execi 600 ssh user@domain.com 'uptime'}
```HTH.

---

