---
title: "squid accel setup  produces  apache and new user squid ??"
date: 2012-01-17
forum: General Help
---

### Post by jackson21 on 2012-01-17
Dear, Readers, Ubuntu 11.10 here
Setting up squid with  http_port 3128 transparent
and:  visible_hostname localhost.localdomain  so far has
always worked in producing  web  speed increase with the browsers.
But now I am presented with a new login at startup  screen of system
as:
Guest anon login ????? (no valid password of course)
What is this ?
When shutting down the system  I notice among others 

"shutting  down apache2  server " ????

I have never in my life set up or used apache ???

Is squid  accessible now only with a different login ?

On the other hand the browsers (Firefox, Chrome) run smoothly with the proxy settings  localhost 3128


Thank you so much for any suggestion

jackson

---

### Post by jackson21 on 2012-01-18
SOLVED:

using squid3 

and http_port 3128 transparent

will do it.

jackson

---

