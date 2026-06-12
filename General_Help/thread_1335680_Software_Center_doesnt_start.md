---
title: "Software Center doesnt start"
date: 2009-11-23
forum: General Help
---

### Post by gauros on 2009-11-23
HI

I tried to install bluej and the software center crashed and does not start anymore.

Whe i try to start it form the command line i get this error

>  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 20, in <module>
    import aptdaemon


Any help would be appriciated

---

### Post by kleskjr on 2010-01-22
I have exactly the same problem with my software center.
Did you get any solution?

I reinstalled aptdeamon, but probably some path should be changed somewhere...

cheers

---

### Post by gauros on 2010-01-22
Hi Mate

During a project i Had to change the default python version from 2.6 to 2.5 and that was the problem, when i changed it back it fixed it
I hope it helps

---

### Post by kleskjr on 2010-03-04
yep, I think I did the same a couple of months ago, but I don't want 2.6 as a default.
should I just change some python path to point the apt-deamon..i googled a bit but did not find anything.

---

