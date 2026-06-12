---
title: "Weird graphic error."
date: 2010-03-20
forum: General Help
---

### Post by Emascu on 2010-03-20
Hello.

I'm using Ubuntu 9.10, and recently I tried to set up a second screen to extend my current laptop. Ever since that moment all my compiz desktop effects are all crazy. I get all lines of other desktops screens scattering all over the pace. The compuz cube effect as exaple as you can see in the screenshot below. As you can see in the screenshot that below the active windows I get some weird graphic error.

[http://img180.imageshack.us/img180/8971/schermafdruk.png](http://img180.imageshack.us/img180/8971/schermafdruk.png)

Before setting a second screen compiz runned just fine. I can only use my laptop now with compiz settings completely disabled. 

Can anyone help me with this one? I'd appreciate the help.

---

### Post by Emascu on 2010-03-20
Anyone, please?

---

### Post by iponeverything on 2010-03-20
try running:

```
sudo Xorg -configure
```

see if it fixes your issues.

---

### Post by Emascu on 2010-03-20
I tried that command and I get this error:

lars@lars:~$ sudo Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
lars@lars:~$

---

### Post by iponeverything on 2010-03-20
maybe:

```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by Emascu on 2010-03-20
No luck unfortunately.

---

### Post by Emascu on 2010-03-20
Wow this forum is fast. A few hours later and this is already on the 6th page. Still I'd like to have this fixed so if someone could please help me out I'd really appreciate it.

---

