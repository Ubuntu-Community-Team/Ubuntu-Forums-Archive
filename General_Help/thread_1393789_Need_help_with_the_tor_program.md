---
title: "Need help with the tor program"
date: 2010-01-29
forum: General Help
---

### Post by robofighter on 2010-01-29
I am using the program tor, and I am having problems with websites using SSL.

All other webstites work fine, slow but fine with ip address from half way across the world.

However when ever I go to a website that uses ssl encryption at any process it just stays a white page and doesn't load anything.
Without it, I can't logon to anything, even my own e-mail.

Also I am using the latest tor program from the tor project's own repository and I am running Ubuntu 9.10

---

### Post by Robert Lutken on 2010-01-29
Hi
I think this is because tor blocks any plug-ins, history , cookies every little vulnerability therefore making it safer to use.

i highly doubt  that you will be able to use any webages with any login procedure

im sorry but this is just the way tor works or from my knowledge anyway 

please see [http://www.torproject.org/download.html.en#Warning](http://www.torproject.org/download.html.en#Warning) for more info

---

### Post by robofighter on 2010-01-29
Then how the hell do people get their e-mail through tor?
Most logins requires the use of HTTPS.

---

### Post by Silvereyes on 2010-03-07
TOR does not block anything.

It is simply a 'router' which routes traffic back and forth between source (your machine) and destination (website) over an encrypted link. Nothing more.


Are you running any ad or script blocking software? ie. privoxy, adblock, noscript etc.

Try disabling these (one at a time then all at once) and see if the problem still occurs.

---

