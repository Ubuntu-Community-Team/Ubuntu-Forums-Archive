---
title: "Strange problem with torchat on Ubuntu 11.10."
date: 2012-04-04
forum: General Help
---

### Post by mihoo on 2012-04-04
I have strange problem with torchat on Ubuntu 11.10. I can't receive any message just nothing show's. I can write messages to other people also I see them online or offline. I was try everything and have no idea what's the problem.
Please help! :)

---

### Post by philinux on 2012-04-04
Post moved to own thread.

---

### Post by mihoo on 2012-04-04
I have error when I run torchat in terminal: 
Apr 04 23:44:07.087 [notice] Closing stream for '[scrubbed].onion': hidden service is unavailable (try again later).
I try change path in torrc to:
a) hidden_service/
b) /home/(username)/.torchat/hidden_service/
c) /var/lib/tor/hidden_service/
still the same... any idea?

---

### Post by mihoo on 2012-04-04
Heh,
HiddenServiceDir hidden_service
in file
/usr/share/torchat/Tor/torrc.txt
works fine there is no errors now but sill I can't recive anything and torchat increase CPU usage  from 40% to 80% :(

---

### Post by mihoo on 2012-04-06
After update to ubuntu 12.04 problem disappear into thin air ;)

---

