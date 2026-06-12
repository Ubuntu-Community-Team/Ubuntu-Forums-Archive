---
title: "Clone, Virtualize or Ghost? Need orientation"
date: 2011-07-29
forum: General Help
---

### Post by rgambra on 2011-07-29
Hi all, i need a litle orientation i am kind of lost about what is the proper solution that i should use.

What do i have? I have an Ubuntu installed with an ERP, PostgreSQL, ssh, vnc, etc, all configured in a "generic" way.

What do i need? I need to be able to copy or replicate that ubuntu configuration with all packages and files to a new PC (Different Hardware)

I have been reading a lot, and i reach to 3 posible solutions:
Clone: I think im going to have hardware problems
Ghost: Idem Clone.
Virtualize: Going to lose some performance.

I would like to know your experiences, if any here have done samething like that, and what solution (and software) have you used.

Thanks!

---

### Post by lmarmisa on 2011-07-29
Try remastersys. This package was included in different versions of Ubuntu but apparently not in 11.04.

```

sudo apt-get install remastersys 

```

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

[http://bikramkawan.com.np/how-to-install-remastersys-on-ubuntu-11-04-natty-narwhal/](http://bikramkawan.com.np/how-to-install-remastersys-on-ubuntu-11-04-natty-narwhal/)

---

### Post by jerrrys on 2011-07-29
you may be looking for [clonezilla]("http://clonezilla.org/")

EDIT: as far as different hardware, ubuntu carries a pretty good arsenal and if you got internet access at time of install on another machine you should be able to load any additional packages you need.

---

### Post by rgambra on 2011-08-04
Thank you, im going to try clonezilla and see how it goes.:D

---

### Post by jerrrys on 2011-08-04
TIP:  the "beginner mode" is what i use.  makes it real painless :)

---

