---
title: "Tor with Google Chrome"
date: 2011-09-22
forum: General Help
---

### Post by Primefalcon on 2011-09-22
Ok first off I have install tor and vidalia and all that stuff...

I stated it up and got it showing the green onion..

however when I open chrome and set up the proxy settings to http to 127.0.0.1 for 8118 and such...

it's not working, says it cant reach the proxy server

---

### Post by mutley89 on 2011-09-22
Are you sure about the port number, tor uses 9050 by default.

---

### Post by Primefalcon on 2011-09-22
> **mutley89 said:**
> Are you sure about the port number, tor uses 9050 by default.
I set that or the socks proxy but I'll give that a try for the http now

---

### Post by Primefalcon on 2011-09-22
no luck

---

### Post by mutley89 on 2011-09-22
Are you using the settings menu inside chrome?  If so try starting chrome with
```
google-chrome --proxy-server=socks://host:port
```

---

### Post by Primefalcon on 2011-09-22
NO joy :-(

---

### Post by mutley89 on 2011-09-24
[FONT=Arial][SIZE=2]Firefox works okay, but chrome gives "Unable to connect to proxy server", yes? 

Wh****at is the output of :

[/SIZE][/FONT]```
netstat -l | grep 'tcp\>'
```

---

