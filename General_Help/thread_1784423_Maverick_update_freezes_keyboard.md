---
title: "Maverick update freezes keyboard"
date: 2011-06-16
forum: General Help
---

### Post by revjmcaldwell on 2011-06-16
I can't boot Maverick Meerkat after a rather massive update (about 750 MB).  When I get to the login screen I can't enter my password because the keyboard simply fails to work.

Any ideas?

---

### Post by An Sanct on 2011-06-17
> **revjmcaldwell said:**
> I can't boot Maverick Meerkat after a rather massive update (about 750 MB).  When I get to the login screen I can't enter my password because the keyboard simply fails to work.

Any ideas?

Welcome to the forums!

What was that update??? I am also on Maverick and for the last few weeks, updates where not larger than 15Mib. Was it an "Version update"?

Where you maybe prompted for a "Partial upgrade"? (that's a bad thing...)

The solution could be to hold shift while booting and from there select an administrator console/terminal with networking (I don't remember the exact phrase right now...) and updating again from there.

---

### Post by revjmcaldwell on 2011-06-17
Yes, I was prompted for a "partial upgrade."  Why, I hesitate to ask, was that a 'bad thing'?

---

### Post by revjmcaldwell on 2011-06-17
I'm still not sure what happened, but I used 
```

apt-get dist-upgrade
```

and let it do its thing for a couple of hours while it downloaded and then answered "Y" to pretty much every question.  In the process, of course, I've installed 11.04!  Everything seems to be working as it should.  

Mark this one solved! :D

Thank you for your help.  And it's good to be here.

---

