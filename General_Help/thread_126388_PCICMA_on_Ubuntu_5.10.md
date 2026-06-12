---
title: "PCICMA on Ubuntu 5.10"
date: 2006-02-06
forum: General Help
---

### Post by beko1987 on 2006-02-06
Hi Guys. Linux Newbie here! I ordered the free cds and their great. Installed it on my thinkpad T20 700mhz, 128mb 12gb hard drive. All is good apart from my network. I use a wireless PCICMA card. A 3com 3CREW154G72 Office Connect 11g card. When I installed it was plugged in, and it detected it, but I dont know the specifics of my network, simply how to connect whilst in the desktop, so I skipped the step. Now when I plug the card in in the GUI it isnt recognised, no lights come on, nothing! Any idea on how to set it up?

Going to become familiar with it on my laptop then put it on my pc. I booted from the live cd and that was fantastic, even my Logitech MX5000 desktop set, which are advertised as XP only worked flawlessley!

cheers.

Sam\\:D/

---

### Post by hajk on 2006-02-06
Why not use the live-CD once more to start your ThinkPad, chances are that it recognizes your PC-Card (PCMCIA) wireless card. Then all you have to do is check which driver was loaded for it - check /var/log/syslog and /proc/modules to get an idea. And also check /etc/network/interfaces. What you learn there can then be used to solve the connection problem on your installed Ubuntu.

---

