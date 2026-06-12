---
title: "Firefox slow / Network question"
date: 2005-03-13
forum: General Help
---

### Post by alpen on 2005-03-13
Hello: I am a TOTAL ubuntu/linux/unix newbie. I installed ubuntu on my laptop yesterday and I expect this will be the first of many questions.

first up: I hope this is the correct forum, should I be in the Desktop support forum or installation forum?

I have a DSL connection to the internet & a wireless LAN. the ubuntu install detected the wlan card & connected to the internet with no intervention by me (I was very impressed by that!).

My problem is firefox is very slow when looking for new pages/sites. A message 'Resolving host www.x.y' is displayed and the page is displayed a minute or more later. Here's what I've done to try resolve the issue:

In Network Settings / DNS there were 2 entries (not put there by me), one was the IP address of my DSL router and the other was 158.43.240.4 which is some network site in the Netherlands (I'm in the UK) which I guess resolves domain names. I deleted both entries (coz Windows has no entries) but this had no effect - firefox still slow.

Then I checked the forums here and there was a suggestion to turn off IPv6 (whatever that is) so I did the following:
sudo nano /etc/modutils/aliases
and removed the initial '#' from the following line
# alias net-pf-10 off # IPv6

then
sudo update-modules

This made things worse & internet sites could not be found at all so I've now reverted to the original config (2 entries in DNS, IPv6 turned back on) & it's still slow.

any other suggestions??

rgds

---

### Post by alpen on 2005-03-13
Pls disregard the above post. I did some further searching & found the following thread:
[http://www.ubuntuforums.org/showthread.php?t=10339&highlight=firefox+slow](http://www.ubuntuforums.org/showthread.php?t=10339&highlight=firefox+slow)

It showed a different way to disable IPv6 (within firefox) - on this occasion it worked.

---

### Post by amerigo5 on 2005-03-18
This problem happens not only with Firefox but also with Mozilla browser.

Even after disabling IPv6 (network.dns.disableIPv6=true), the problem remains.

Just a note: this problem started when I recently updated my system (thru Synaptic) a few days ago. Could this issue possibly caused by system update? Thanks.

---

### Post by mirtux on 2005-03-30
I've got the very same problem.... no way to resolve it with the ''about:config'' procedure..

regards,
MC

---

### Post by amerigo5 on 2005-03-30
After upgrading to Hoary Preview, everything is back to normal. Thanks.

---

