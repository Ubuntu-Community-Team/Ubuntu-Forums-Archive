---
title: "Hardware &amp; wierd internetproblems.."
date: 2010-10-05
forum: General Help
---

### Post by mynthix on 2010-10-05
Hi there, ive had ubuntu now for 2 days. Since the first run problems have been shown and ive tried finding the answers. 
But my internet problem is making it hard.

To the problem:
When wired connection, i can ONLY connect to google. No other site are connectable. I can ping facebook with a ms of 134. And i am able to connect to my msn via empathy with a really long connecting time.

Wireless connection sais: Device not ready.

Ive tried to solve the wireless problem reading other posts about the rt3090. But during the install it need to download some files. which doesnt work because the only site i can access is google (using wired to download).

Ive got a MSI CX600 and i would really need some help during this bad period :'( ..

Thanks !!!

---

### Post by searchfgold6789 on 2010-10-05
I would assume you would need files/drivers for your wireless card.
I would just get them on a different computer (i.e. at a library) and put them on a USB stick or CD-R.

---

### Post by mynthix on 2010-10-05
> **searchfgold6789 said:**
> I would assume you would need files/drivers for your wireless card.
I would just get them on a different computer (i.e. at a library) and put them on a USB stick or CD-R.

Yepp i have, but as i said, the computer needs to connect to internet for downloding external files. which i cant get on a non-linux computer. 

And still, can only connect to google, using wired..

---

### Post by TBABill on 2010-10-05
Sounds like a DNS server issue. Have you tried another proxy server to see if it fixes your wired issue? 
 
[_[COLOR=#0000ff]http://ubuntuforums.org/showthread.php?t=1587288[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1587288")
 
Edit: is it possible you aren't actually connecting to Google but rather the system loading a cached Google page?

---

### Post by mynthix on 2010-10-05
> **TBABill said:**
> Sounds like a DNS server issue. Have you tried another proxy server to see if it fixes your wired issue? 
 
[_[COLOR=#0000ff]http://ubuntuforums.org/showthread.php?t=1587288[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1587288")
 
Edit: is it possible you aren't actually connecting to Google but rather the system loading a cached Google page?

I will try that out soon, ehm, yeah, im able to search in google on any keyword. but i cant connect to any of the links..

EDIT: grr, this didnt help. I wonder why i only can access google but nothing else.. Or, i can ping facebook with a ms of 134. And go on empathy with a really long connecting time to the accounts. And still havent got the wireless working either.. "/

---

### Post by TBABill on 2010-10-06
I am not sure why you can't go beyond Google. Why is it special enough to work? I have had DNS issues on all machines, both Windows and Linux. So I went into my router setup and entered that DNS server so all my machines would stop sitting and looking for sites so long. Worked like a champ and I didn't have to do it to each machine individually.
 
Do you have the ability to try that? It's a shot in the dark and may not even be the problem but I'm stumped why you can get Google AND get search results, but not be able to actually navigate to them (assuming IPV6 is already disabled).

---

### Post by mynthix on 2010-10-06
> **TBABill said:**
> I am not sure why you can't go beyond Google. Why is it special enough to work? I have had DNS issues on all machines, both Windows and Linux. So I went into my router setup and entered that DNS server so all my machines would stop sitting and looking for sites so long. Worked like a champ and I didn't have to do it to each machine individually.
 
Do you have the ability to try that? It's a shot in the dark and may not even be the problem but I'm stumped why you can get Google AND get search results, but not be able to actually navigate to them (assuming IPV6 is already disabled).

Yepp, IPV6 is disabled. i think (a) i've followd some tutorials about it. and it should be disabled.
Just made this adjustment and im gonna try it out now.

EDIT: This did not make any diffrence.. I am able to connect as i said to my msn via empathy, but the connection time is very long. And i can ping Facebook, ttl=246 and time=175ms . but if i try to connect to facebook via chrome or firefox, it just loads, but never connect to the site... Is there no one who can help me "/

---

### Post by mynthix on 2010-10-07
Bump

---

### Post by mynthix on 2010-10-09
bump

---

