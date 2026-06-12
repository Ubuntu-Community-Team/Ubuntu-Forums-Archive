---
title: "Send Fax directly from your modem port"
date: 2009-09-18
forum: General Help
---

### Post by bvidinli on 2009-09-18
I need this and found some answers, here I share with you,

Step 1: install some fax software:
aptitude install gfax efax efax-gtk sl-modem-daemon

Step2: read this:
[http://ubuntuforums.org/showthread.php?t=234456](http://ubuntuforums.org/showthread.php?t=234456)

normally that give some errors in efax-gtk,
but package sl-modem-daemon fixes those errors.. 
in efax-gtk, file, settings, modem->serial device, change to "modem"

fax entry method should be socket..

---

