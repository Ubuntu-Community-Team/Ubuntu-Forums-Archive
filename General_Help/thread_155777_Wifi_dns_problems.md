---
title: "Wifi dns problems"
date: 2006-04-05
forum: General Help
---

### Post by Dafydd on 2006-04-05
Hello,

I connect to several networks every day... My home network (d-link router) works fine except... Ubuntu 5.10 keeps rewriting the dns name servers which means certain programs don't really work on internet (dillo, gaim etc).

is there any way of fixing this without hacking in a way that requires rehacking every time i switch networks?

i edited sudo /etc/dhcp3/dhclient.conf and commented out the relevant sections in etc/dhcp3/dhclient-script 

but this then makes switching networks a nightmare...

dafydd

---

