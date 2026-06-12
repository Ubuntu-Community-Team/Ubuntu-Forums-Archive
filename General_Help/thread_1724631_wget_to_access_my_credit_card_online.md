---
title: "wget to access my credit card online"
date: 2011-04-08
forum: General Help
---

### Post by bradshaw_k1te on 2011-04-08
wget,   I am interested in making wget do a slightly different function for me.  I have downloaded it, built it (1.12) and it works perfectly right out of the box.

I would like to have it login to my creditcards.citi.com https website, give my **[COLOR="Red"]user id[/COLOR]**, my [COLOR="Red"]**password**[/COLOR] and **[COLOR="Red"]"select NEXT-SCREEN label=Account Activity"[/COLOR]**, then [COLOR="Blue"]***capture the account activity ***[/COLOR]that returns.

I got these three values in my firefox Selenium script that runs perfectly time after time.

My big picture goal, is to be able, on a crontab, to dump my account activity every night at midnight.

I am not married to this idea if anyone has a better or different route.

Thanks, Bradshaw :popcorn: to any helpers! :KS

---

### Post by galvatron408 on 2011-07-31
sounds like you should investigate curl and give up on wget. i'm pretty sure curl will do what you want.

---

