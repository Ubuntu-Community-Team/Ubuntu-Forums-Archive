---
title: "Russian and Chinese Servers"
date: 2011-11-07
forum: General Help
---

### Post by dougw4 on 2011-11-07
This is making me really nervous! I'm using Ubuntu 11.10 with Firefox 7.0.1. Firefox has an addon called Domain Details 2.6.9.1. Whenever I go to an Ubuntu related web site, Domain Details reveals that the server is located in either Russia or China. Is this legitimate?

Some of the IP's are:
91.189.89.88
91.189.89.161
91.189.90.40
91.189.94.12

---

### Post by duke.tim on 2011-11-07
The last ip seems to be legit. The rest just show an error when browsed to.

I did a Whois query on them and they are either located in GB , United Kingdom, or The Isle of man. Which is not russia or china

Just in case the whois query was incorrect I traced the route to the server and it goes through the correct path to be in Great Britain somewhere. (unless it was redirected after the trace hit a firewall, which I doubt that it was redirected)

Likely the plugin is either buggy, or buggy and reporting the wrong IP address.

---

