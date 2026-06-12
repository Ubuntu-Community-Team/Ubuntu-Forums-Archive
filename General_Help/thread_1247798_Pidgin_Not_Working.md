---
title: "Pidgin Not Working"
date: 2009-08-23
forum: General Help
---

### Post by twallace on 2009-08-23
Never have been able to get Pidgin to work properly. It will pull up ny new emails ok but the IM feature has never worked right. 

Can't see any of my contacts from MSN, Yahoo, or GMail accounts. And my MSN account keeps getting this error:

Connection error from Notification server:
Writing error

Any ideas???

---

### Post by Kerubu on 2009-08-23
Can you post what version of Ubuntu you are using and what version of Pidgin ?

---

### Post by twallace on 2009-08-23
9.4 and 2.5.5

---

### Post by Kerubu on 2009-08-23
Hmm same as me and I'm working ok. Perhaps just a bad install if Pidgin ?

Tried purging your system of pidgin and re-installing ?

```
sudo aptitude -purge remove pidgin
```

** Note check dependencies that will be effected, it will tell you this when you give the above command.

You could then try installing again with :

```
 sudo aptitude install pidgin 
```

Of you could go to the developer's website and follow their instructions to get 2.6.1 :

[http://www.pidgin.im/download/ubuntu/]("http://www.pidgin.im/download/ubuntu/")

---

### Post by Kerubu on 2009-08-23
In fact I would upgrade to 2.6.1 there are a few problems with versions 2.5.5 and below. Follow their instructions on their website. Ingore what I said about about removing.. probably no need to if you go to their website and follow their instructions

---

