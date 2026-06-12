---
title: "Difficulty configuring handler app for SLurl on Natty"
date: 2011-10-12
forum: General Help
---

### Post by drknot on 2011-10-12
Hello.
I run one 64 bit laptop in Maverick and a 32 bit Natty.

I have had to install Imprudence to access some college training and can run OSGrid on both machines.
I have successfully managed to get the Maverick machine to handle and redirect SLurl by configuring the necessary about:config changes in Firefox ie

add:
network.protocol-handler.external.secondlife boolean=true
network.protocol-handler.app.secondlife string= /home/path-to-imprudence/handle_secondlifeprotocol.sh
First try launched a dialog to associate the necessary program with secondlife://

On Natty - same deal but only getting a "Firefox does not know how to handle this protocol (secondlife)

I am stumped as to what else I can try.

Firefox from repository on both :
7.0.1 on the Natty, 3.6.23 on Maverick
Same issue with no link/re-direct using Chromium so I am assuming not a Firefox bug

Hints?

Cheers

---

### Post by Jaguar07 on 2012-07-25
In Firefox
about:config
add boolean 
network.protocol-handler.expose.secondlife
value FALSE

---

