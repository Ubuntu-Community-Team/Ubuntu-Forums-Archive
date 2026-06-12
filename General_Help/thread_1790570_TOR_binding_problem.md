---
title: "TOR binding problem"
date: 2011-06-25
forum: General Help
---

### Post by miko5054 on 2011-06-25
i installed tor software fowling this link 
[HTML]How to install tor on ubuntu natty 11.04 « goshawk's digital nest[/HTML]

then i set up a port on chrome proxy switchy and it was working fine. 

today it`s buged and the eroor message was received by tor lokk like that
```
 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
```

i was this link to try to resolve  the problem but i cannot 
Ubuntu Forums
[HTML]http://ubuntuforums.org/showpost.php?p=9226418&postcount=3[/HTML]

???

---

### Post by miko5054 on 2011-06-26
i solved it by edit the tor config file

on terminal
```
sudo gedit  /etc/tor/torrc

```

than edit port 9050 TO 9051
and on vidalia setting as well TO 9051

---

