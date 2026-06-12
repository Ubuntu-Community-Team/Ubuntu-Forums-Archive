---
title: "Ubuntu can't access xtra.co.nz"
date: 2009-12-14
forum: General Help
---

### Post by Twotoes on 2009-12-14
Ubuntu can't access xtra.co.nz
I put Ubuntu 9.10 recently on a friend's PC, the only OS he has, and it worked very well for several weeks but when he tried to connect to his ISP xtra.co.nz this morning with Firefox or Thunderbird he had no success. Using my laptop I was able to connect using Vista but not when I switched to Ubuntu 9.10. Ping test was OK on Ubuntu.
I was told by the help desk operator that the connection was OK but Xtra didn't support any Linux system so if one wasn't using Windows you were out of luck.
Has anyone else had this problem and found a solution?

---

### Post by kreggz on 2009-12-14
is it via an ADSL modem or router?

---

### Post by Twotoes on 2009-12-14
Yes

---

### Post by tommynz1975 on 2010-03-09
This is an old thread but I thought before the Mods close it
I would post my solution

Open Terminal

Applictions --> Accessories --> Terminal
and type

```
sudo /etc/init.d/networking restart
```

It may take a few minutes to do its thing.

I use the adsl modem provided by xtra and a netgear router. This seams to work for me..

This is unfortunate that Telecom will not employ a few stuff that understand linux

---

### Post by lisati on 2010-03-09
<rant about Xtra customer service deleted>
These are the guys whose "PC Health check" web page advised me to "upgrade" from IE8 to IE6 or IE7, so its hardly surprising that you'll have some fun trying to get support for your Linux installation...... (/me wonders if this has something to do with the setup CD for my current modem/router not running to completion the last time I tried. It went to the "wrong" web page part way through. It's one of their freebies. No big deal, a bit of googling got hold of a copy of the modem manual that was missing when the modem was delivered.)

---

