---
title: "Starting Apatche2 at boot Up, plus configring it over LAN"
date: 2011-04-17
forum: General Help
---

### Post by shadramon on 2011-04-17
[SIZE=3]Hey guys 

Could anyone please help me to configure my Apatche server to start at Boot Up. I  started 'Start Up Application' under > 'System' but didn't know what to do then.

How to make Apatche configured to be used over LAN. Btw i have it already up and running and i can accesses the web pages through my browser.

Cheers.
[/SIZE]

---

### Post by AlexDudko on 2011-04-17
Run
> sudo chkconfig apache2 on
in terminal and reboot, your web server will be up and running after reboot and any other time you start your sever.

---

### Post by shadramon on 2011-04-17
The cod is incorrect :(
```
sudo: chkconfig: command not found

```

---

### Post by AlexDudko on 2011-04-17
> **shadramon said:**
> The cod is incorrect :(
```
sudo: chkconfig: command not found

```

The code IS correct.
> sudo apt-get install chkconfig
> sudo chkconfig apache2 on

---

