---
title: "email me libwine and wine please"
date: 2006-02-18
forum: General Help
---

### Post by professor_chaos on 2006-02-18
Ok, so I upgraded to wine 0.9.8 thinking if I still had problems with dvddecryper I would just reinstall wine and libwine packages version 20050310-1.1

But now I can't find them and debians repository where I found them before is down. Can someone either point me in a direction where I can find them or email me the .deb's. Appreciate it. I need both wine and libwine version 0.0.20050310-1.1

[email]dan.collins@uchsc.edu[/email]
Thanks

---

### Post by SWAT on 2006-02-18
Option 1 (I recommend this): Download the Wine sources and configure/make/install them manually (I always do this)
Option 2 (not for beginners or people who don't want beta stuff): [Try the Wine CVS version](http://www.zwhlug.nl/content/wine_a_wine_cvs_howto)

---

### Post by professor_chaos on 2006-02-18
And your compiled versions of wine work fine with DVD decrypter and DVD Shrink?

---

### Post by professor_chaos on 2006-02-19
I compiled wine 0.9.8 and yes it does work for DVD shrink but not DVD decrypter.

Same ole damn "no devices detected"

---

### Post by professor_chaos on 2006-02-19
nevermind. Although I followed mr basses instructions, I found another thread here that suggested using "winecfg".

I installed wine through synaptic to get the libwine libraries and then compiled wine. So I guess my ~/.wine/config system setting of nt40 wasn't being read by the compiled version.

Well it's kinda cool, because I didn't know about winecfg. Great interface.

---

