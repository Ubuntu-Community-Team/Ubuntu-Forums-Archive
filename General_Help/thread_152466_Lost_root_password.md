---
title: "Lost root password"
date: 2006-03-29
forum: General Help
---

### Post by mhinton539 on 2006-03-29
This has to qualify as explanation of "why you don't do installs late at night"...

Having installed kubuntu for the very first time (on my rather ancient Mac), I began using it, then reached the point where I needed to su. Oops. I don't recall entering a root password during installation...but evidently I must have done so... Anyway, is there a way to obtain or override-set the root-password...or do I have to re-install (and pay attention this time)...

Thanks,
Mark

---

### Post by aysiu on 2006-03-29
You're cool. There is no root password.

Read more here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by mhinton539 on 2006-03-29
Aysiu -

Thank you very much! That's just the way Mac OS X does things - root disabled, no su, use sudo. I feel at home already!  :) 

--Mark

---

### Post by rfruth on 2006-03-29
aysiu said it, your mac is like Ubuntu (or is it the other way around) there is no SU use SUDO

---

### Post by ozorba on 2006-03-30
[QUOTE=rfruth]aysiu said it, your mac is like Ubuntu (or is it the other way around) there is no SU use SUDO[/QUOTE]


You can set a separate root password if you want to.

sudo su

and once in the su shell type passwd and enter your root password.

Cheers,
OZ

---

### Post by MJN on 2006-03-30
Or even **sudo passwd root**

---

