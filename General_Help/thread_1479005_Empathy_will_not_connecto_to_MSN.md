---
title: "Empathy will not connecto to MSN"
date: 2010-05-10
forum: General Help
---

### Post by bshosey on 2010-05-10
I noticed today after applying all update I get Network error when trying to connect to MSN with empathy. Any one else having this problem and what can I do to resolve this.

I am running ubuntu 10.4
did not have any problems all day Friday.

---

### Post by bshosey on 2010-05-10
OK I figured it out I just did a 

Kill all telepathy-butterfly and restarted empathy.

---

### Post by x-shaney-x on 2010-05-10
Apparently, it is a problem related to accounts not ending in hotmail.x (for example live.co.uk or other addresses).
I uninstalled telepathy-butterfly, though I did have to re-create my account.

---

### Post by d3ngar on 2010-05-11
This worked for me too... 
I'm using my gmail email as MSN messenger account.

Without telepathy-butterfly all works perfect.

thanks!

---

### Post by VictorHugo11 on 2010-05-20
Yeah, but what's the exact command??! Do I just type in "Kill all telepathy butterfly" and press enter??

---

### Post by x-shaney-x on 2010-05-20
You would need to kill telepathy-butterfly EVERY time you run empathy.
If you have non-hotmail msn accounts it would be better to remove the telepathy-butterfly package (apt-get remove telepathy-butterfly).
If memory serves me correctly nothing else is removed with it and you can always keep tabs on development of empathy and re-install butterfly if the situation changes.

---

### Post by psychok7 on 2010-06-11
> **bshosey said:**
> OK I figured it out I just did a 

Kill all telepathy-butterfly and restarted empathy.

thanks this worked for me also.. have a gmail msn account,ubuntu 10.04 updated

---

### Post by johnuk on 2011-02-14
Same problem, I can see MSN contacts online and they can see me, but no messages.

Tried multiple different servers and port numbers. No luck.

Removed butterfly, instantly works.

Thanks! ;)

---

