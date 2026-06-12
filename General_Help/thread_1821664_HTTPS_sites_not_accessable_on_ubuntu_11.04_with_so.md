---
title: "HTTPS sites not accessable on ubuntu 11.04 with solution"
date: 2011-08-09
forum: General Help
---

### Post by deva99 on 2011-08-09
i hav the problem ...n i am having solution for it. ...i searched a lot on forum .but didnt find any proper solution for my problem. 


problem : " Cannot access some sites on Ubuntu 11.04 specially  HTTPS sites. loading of certain sites was really slow" 


Solution : well. i found no one who could gave me solution that worked. so i studied some linux n here is solution ..

ON terminal : sudo pppoeconf

then just follow instructions ...set to default every thing. it will configure all ur net settings on its own.
restart ur pc. no need to dial anything. the net will auto dial itself without any problem..
just make sure...u do it correctly ..read instructions...


if u find this help full. plz reply :guitar:

n my question is... plz explain pppoeconf what is it ..n function

---

### Post by dino99 on 2011-08-09
"User-friendly tool for initial configuration of a DSL (PPPoE) connection."

but if you have used it, then you know it right ?

---

### Post by Frogs Hair on 2011-08-09
The link is for Debian , which Ubuntu is based on . Please use complete words in your posts .  [http://wiki.debian.org/PPPoE](http://wiki.debian.org/PPPoE)

---

### Post by deva99 on 2011-08-09
ya..i got that...but i am asking..can it help in detecting...wireless connection and all? ....for suppose i am on mobile net...using nokia pc suite...can i configure this internet on ubuntu using this tool...exactly how does it function..? 


i dont know about debian stuff..but thx..m new..to ubuntu ...

---

### Post by dineshs on 2011-08-10
pppoe is point to point protocol over ethernet.To create DSL connection over ethernet or wifi you can use [COLOR="blue"]sudo pppoeconf[/COLOR] (Terminal method).
Regarding mobile broadband you need [COLOR="Blue"]sudo pppconfig[/COLOR] or [COLOR="blue"]wvdial[/COLOR] (Terminal method).Both DSL and mobile broadband can be easily configured via network manager (GUI).
> problem : " Cannot access some sites on Ubuntu 11.04 specially HTTPS sites. loading of certain sites was really slow" The reason I think is MTU.pppoeconf uses 1452 as MTU while network manager uses 1500(default).You can change MTU anyway.

---

