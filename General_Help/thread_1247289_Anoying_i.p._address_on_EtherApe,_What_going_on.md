---
title: "Anoying i.p. address on EtherApe, What going on?"
date: 2009-08-22
forum: General Help
---

### Post by VipX1 on 2009-08-22
This is actually a bit freaky. I've a particular i.p. that is showing up on EtherApe and filling up the hole screen with Orange. The protocol it seems to be always using is HTTPS (red) but when it fills up the whole screen, doing a search or whatever it's orange. When it started I noticed because the light on my network switch, the light for my desktop termination flash constantly like I was downloading something only I wasn't. Then I looked at EtherApe and it was as I've described already.
What I was doing when all this started was verifing a site on W3C and then I installed Komodo-edit-5. I hope there's a simple connection between all those things. I entered a new rule into UFW to deny the i.p. and reloaded, didn't work. So I rebooted, still there. Then I switch off all my on-line services Skype, Spideroak my email but the i.p. is still there. I have nothing open only EtherApe (as root) and the i.p. is still there. So I killed eth0 and used my laptop which is on the same network but doesn't have the same problem with the anoying i.p.

Why didn't my ufw rule stop it? sudo ufw deny and then the i.p. I tried with proto and rcp and then with udp and niether worked. I have the GUI gufw instaled but that doesn't let me block i.p.'s

Is it alright to mention the i.p. here?

---

### Post by VipX1 on 2009-08-22
It's spideroak. It must be active even when the service is off, or looks like it's off. I didn't check the processes. I started Spideroak on the laptop and there was the i.p. I don't know why I never saw that before. It trace back to Newark and I thought Spideroak was based in the U.K.  - i.p. starts with 204.180.*.*

---

