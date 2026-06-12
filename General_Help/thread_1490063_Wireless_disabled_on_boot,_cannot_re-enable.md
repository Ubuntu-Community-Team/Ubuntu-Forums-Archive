---
title: "Wireless disabled on boot, cannot re-enable"
date: 2010-05-21
forum: General Help
---

### Post by deliriousthunder on 2010-05-21
Hi,

I have recently installed 10.4 (wubi installation), and am having strange problems with my networking.

It was working fine, wireless enabled, connecting to my network fine. Then for what seems like no reason, it decided to disable the wirless on boot, and I cannot re-enable it, the option to enable it (by right clicking the nm applet) is greyed out.

I have had this problem twice now, the first time it happened, my ubuntu installation was really new, so I just reinstalled, no harm done. The second time I did something that seemed to fix it (for a while at least), but now that is not working.

Help would be appreciated, it's driving me crazy.

Thanks,
Tom

---

### Post by deliriousthunder on 2010-05-29
bump

I cannot figure this out, and it renders my ubuntu installation useless. Does no one even have any suggestions?

---

### Post by schatoor on 2010-06-06
> **deliriousthunder said:**
> bump

I cannot figure this out, and it renders my ubuntu installation useless. Does no one even have any suggestions?

Hi, try this:

sudo service network-manager stop
cd /var/lib/NetworkManager/
sudo rm NetworkManager.state
sudo service network-manager start

---

### Post by schatoor on 2010-06-06
Actually, to elaborate some more, I have had the same problem as you did. I have a acer 3810tz with an Atheros Communications AR8131 Gigabit Ethernet wireless card. I found the above instructions on the web with some searching. And it sort of worked for me, although sometimes my wireless gets disabled again, seemingly for no reason. A reboot sometimes helps, or else I have to prompt the commands in a console to get wireless working again. 

This is annoying. If someone has a better solution, we would certainly want to know about it!

---

### Post by schatoor on 2010-06-06
p.s.: deliriousthunder, I would advice that the next time you go to forums to ask for help, give some more info about your machine. Which brand do you have? What model? What relevant hardware is in there (e.g. if you have a wireless problem, what wireless card etc. You can find out by doing "lspci" at the command prompt) Also, what have you tried already? How did that work out?

---

### Post by Rippy on 2010-06-26
I also have an Acer 3810TZ, had the exact same problem, and schatoor's solution worked. I'm happy Ubuntu was the problem, because I was afraid the wireless card may have died (no wireless activity light, pressing the button wouldn't enable/disable it).

Hopefully this will be fixed in an update soon? I thought Ubuntu 10.4 fixed my wireless problems, since in the last version (on this same laptop) it was always dropping my wireless connection and requiring a restart to re-enable...

---

