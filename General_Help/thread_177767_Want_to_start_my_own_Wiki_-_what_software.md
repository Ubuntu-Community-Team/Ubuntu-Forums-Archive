---
title: "Want to start my own Wiki - what software?"
date: 2006-05-16
forum: General Help
---

### Post by codified on 2006-05-16
Hi,

Does anybody know what the Ubuntu team use as the basis for their wiki?  Can anyone make any recommendations?  I'd like to start a wiki on our server - fully self contained (ie. not host externally, as data may be sensitive).

Appreciate any help, thanks.

---

### Post by kspringer on 2006-05-16
Check the credits page on the wiki page [here]("http://wiki.ubuntu.com/wiki/credits").
You might also look at [here]("http://moinmoin.wikiwikiweb.de/") for the main wiki engine.

Hope this helps...

---

### Post by elamericano on 2006-05-16
There's lots to choose from:

[http://c2.com/cgi/wiki?TopTenWikiEngines](http://c2.com/cgi/wiki?TopTenWikiEngines)

---

### Post by az on 2006-05-16
They use moin moin.

---

### Post by codified on 2006-05-16
Thanks all!

---

### Post by tread on 2006-05-17
Don't know if you still looking, but I setup twiki in about 10 minutes on Ubuntu. Just install apache2 and dependencies, then twiki and dependencies. Then from /etc/twiki, add the apache.conf info to /etc/apache/apache2.conf and edit /etc/Twiki.cfg to your taste. Restart Apache .. thats about it.

I'm writing from memory here .. if you run into a specific problem will go to my config files and check.

---

