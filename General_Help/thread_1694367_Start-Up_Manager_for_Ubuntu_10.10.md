---
title: "Start-Up Manager for Ubuntu 10.10"
date: 2011-02-24
forum: General Help
---

### Post by Jørn Rudolph on 2011-02-24
:popcorn:

[I][B]Hej There Ubuntu Forums !

Can you please tell me, where to find a start-up manager and install it ?

:KS

So it is possible to set if Ubuntu start or Windows start ...
[/B][/I]

---

### Post by wiggly81 on 2011-02-24
system > preferances > startup applications

is that what you are after?
or..
in terminal run  
```
sudo gedit /etc/boot/grub/grub.cfg
```

---

### Post by clhsharky on 2011-02-24
Jørn Rudolph

Search Software Center for BUM (boot up manager).


Sharky

---

### Post by Frogs Hair on 2011-02-24
The Startup Manager is in the 10.10 software center and is a different application than Startup Applications. Welcome to the forums !

---

### Post by gandaran on 2011-02-24
> **Jørn Rudolph said:**
> :popcorn:

[I][B]Hej There Ubuntu Forums !

Can you please tell me, where to find a start-up manager and install it ?

:KS

So it is possible to set if Ubuntu start or Windows start ...
[/B][/I]
yes you can set which OS boots first
install terminal code
```
sudo apt-get install startupmanager
```

---

### Post by Jørn Rudolph on 2011-03-01
:guitar:

[I][B]Thanks a LOT for your kind help !

Greetings JR
[/B][/I]

---

