---
title: "Software center won't let me install or remove programs"
date: 2012-05-05
forum: General Help
---

### Post by steveray100 on 2012-05-05
I don't know what I did to cause this to happen (see attachment) but I can no longer remove or install software from the software center. Nor do I even know where to start. HELP!

SOLVED IT!

First I ran: dpkg --configure --pending 
Then I ran: apt-get dist-upgrade -f 

then I ran the software center and, everything works fine!

---

### Post by strask on 2012-05-05
Try typing the following in a terminal window and post the results, it might tell us what the problem is:```
sudo dpkg --audit
```

---

### Post by whiskers751 on 2012-05-05
Oh this is a little problem, easy to fix!
```
sudo dpkg --configure -a
```

---

