---
title: "Printer suddenly not found today"
date: 2012-10-09
forum: General Help
---

### Post by Oldhacker on 2012-10-09
Using Ubuntu 12.04 (64 bit) I attempted to print today, and the only option offered was "Print to file" My Samsung ML-2251N had dissapeared from the printer configuration! Bringing up the Printing - localhost "Add printer" and "start service" are both grayed out. 

After many attempts without success, I re-booted back into Ubuntu 11.10 and my printer was found without any input by me and it printed normally!

I welcome some knowledgeable assistance.

---

### Post by oldfred on 2012-10-09
My first suggestion was to make sure it was plugged in. :)

Someone posted this before, it just purges & reinstalls cups.

apt-get purge cups
apt-get --purge autoremove
apt-get install cups

#In Firefox:
  [http://localhost:631](http://localhost:631)

---

### Post by Oldhacker on 2012-10-10
Thanks for the response. it worked!!!

---

### Post by oldfred on 2012-10-10
Glad that worked. :)

You can change to solved so others searching forum may find answer.

---

