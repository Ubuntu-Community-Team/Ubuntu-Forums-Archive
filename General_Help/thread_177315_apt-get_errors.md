---
title: "apt-get errors?"
date: 2006-05-16
forum: General Help
---

### Post by invalid06 on 2006-05-16
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

That site no longer exists, is there another one that replaces it? or no?

---

### Post by Sutekh on 2006-05-16
I don't know.  For which packages did you add that repository?

---

### Post by invalid06 on 2006-05-16
none, it get that each time i open Synaptic

---

### Post by Sutekh on 2006-05-16
No I mean why did you add that repository?  What packages did you need from there?  If you know we can find a replacement repository.

---

### Post by reazn on 2006-05-16
i also have the same issue.

---

### Post by Polygon on 2006-05-17
i get that every time that i load sypnatic as well, i think the site or something is down

---

### Post by aysiu on 2006-05-17
If you try to go to [http://koti.mbnet.fi](http://koti.mbnet.fi) in your web browser, it redirects to [http://www.mbnet.fi/mbinternet/](http://www.mbnet.fi/mbinternet/)

I don't think the *koti* subdomain exists any more.

---

### Post by elamericano on 2006-05-18
[QUOTE=aysiu]If you try to go to [http://koti.mbnet.fi](http://koti.mbnet.fi) in your web browser, it redirects to [http://www.mbnet.fi/mbinternet/](http://www.mbnet.fi/mbinternet/)

I don't think the *koti* subdomain exists any more.[/QUOTE]

On the other hand, if you go to [http://koti.mbnet.fi/~ots/](http://koti.mbnet.fi/~ots/) then that does exist. What's gone is the ubuntu repository.

Automatix added this, but I don't know what packages it had. I'll post something in that forum.

---

### Post by elamericano on 2006-05-18
Arnieboy says that repository was only hosting a cvs version of amule. You can delete those repositories, and use the regular amule package.

---

