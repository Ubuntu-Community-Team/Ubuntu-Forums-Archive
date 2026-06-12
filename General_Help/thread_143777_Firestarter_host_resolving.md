---
title: "Firestarter host resolving?"
date: 2006-03-13
forum: General Help
---

### Post by Peturrr on 2006-03-13
Just installed firestarter.

I enabled it with no rules set. Everything is blocked, I can't browse anymore. According to the manual this should work... Anyway, I enabled inbound port 80 for browsing, but it didn't work. I added the dns, dhcp, ftp and https port, but still no connectivity.
I can't resolve any hostname with the firestarter firewall turned on.
Is this a bug? Or am I doing something completely wrong here?

---

### Post by Peturrr on 2006-03-13
I solved it.

For some reason I need to enable internet sharing to use my internet connection. I am on a Lan. For internet I need to connect with pppoe to the provider of my university. For some reason Firestarter doesn't allow me to connect to the pppoe connection from my own machine unless I set the connection to shared. Strange...

---

### Post by Sendervictorius on 2006-03-13
Surely you want to allow all outbound connections (permissive by default). This will allow all your pc applications to get out. Only allow inbound connections for services that you want to open - such as a web server on port 80.

---

