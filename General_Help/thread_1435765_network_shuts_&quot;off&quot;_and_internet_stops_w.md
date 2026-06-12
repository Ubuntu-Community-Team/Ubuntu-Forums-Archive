---
title: "network shuts &quot;off&quot; and internet stops working"
date: 2010-03-21
forum: General Help
---

### Post by grimslider75 on 2010-03-21
hi, 

well i just recently erased my hard drive and installed ubuntu 9.10 all over again. I updated as expected and everything was going well, until, my internet stopped working after maybe 40 mins or so after a successful boot. now this same thing happens every 40 mins and i have to reboot the computer by forcing my laptop to shut down by holding down the power button. 

this also made me aware of another problem when restarting or logging off my laptop. the laptop hangs at that terminal-syled screen and the underscore blinks and fails to shut the computer down/log off. i resort to holding down the power button to restart. 

any suggestions/thoughts?????

note: im using a wireless connection with WEP key protection
Atheros network chip
laptop
acer aspire 5532

it just happned again..... im typing now in tomboy notes....
time to restart again...... **sigh**

i also try to open terminal and it fails to function (after the internet stop working), any reason for that?

srry, i would also like to note that the signal strength decreases as time passes by.......

---

### Post by grimslider75 on 2010-03-21
i did the "dhclient" in terminal and it seems that it solved the problem, but ill keep posting the progress

---

### Post by soltanis on 2010-03-22
I'm not sure if Atheros cards have problems with their drivers but I am sure I saw them mentioned somewhere before, probably a manpage for aircrack or something. I think they can't set promisc mode. Or something.

Unknown if this is related, but if you use Network Manager and it has this problem, you might try wicd; it's a solid replacement (and in my opinion much better).

---

### Post by grimslider75 on 2010-03-22
](*,) 

this sucks, 

i installed wicd and now i can't even attempt to access the internet now, no sign of recovery. 

whats mind boggling is that he internet was fine before i erased the partition by mistake, now its giving problems. argh!!!!!

anything i can do? im clueless.

---

### Post by Ancanus on 2010-03-22
Let's see your network application logs.

PROTIP: Just the latest dates detailing any possible errors; remove any personal information.

---

### Post by grimslider75 on 2010-03-22
..

---

### Post by grimslider75 on 2010-03-22
> **Ancanus said:**
> Let's see your network application logs.

srry, how do i do that?

---

