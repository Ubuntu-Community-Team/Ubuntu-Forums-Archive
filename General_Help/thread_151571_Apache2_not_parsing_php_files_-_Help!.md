---
title: "Apache2 not parsing php files - Help!"
date: 2006-03-28
forum: General Help
---

### Post by speedsix on 2006-03-28
For some reason I'm getting an open/download prompt in firefox.

Ive checked the modules available and enabled folders and they seem fine, I've even copied all the apache/php folders from /etc from a working ubuntu machine and still no joy?? If I install PHP5 it works but that removes MythWeb as it depends on PHP4.

Another problem I had was I deleted /etc/apache2 but this wasn't reinstated when I apt-get'd apache2?? I had to copy it back form the other machine.

Many thanks

---

### Post by jacob_lurch on 2006-03-28
Hi

I've had this problem several times....and it turned out the apache/php install was just fine on each occasion.

Weirdly, clearing the cache on the browser did the trick!  You might also wanna try a different browser to see if that presents the same problem.

I really hope this helps.

---

### Post by speedsix on 2006-03-28
Oh my god, you're a star!!

I've been messing around all morning re-install apache/php etc. etc. Tried another browser and it was fine!!

I was even doing ctrl-F5 but that still didn't work??

:cool: 

Thanks again.

---

### Post by jacob_lurch on 2006-03-28
Excellent!

---

### Post by kewlito on 2008-06-27
It worked for me, thanks a lot.

---

