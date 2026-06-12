---
title: "How to Build you own service???"
date: 2012-02-15
forum: General Help
---

### Post by mujahed on 2012-02-15
Hello All,
  
My Problem is:
  
I have script that need to be always run,(waiting),  if I run it from  console it will be in foreground, and I want to keep it in background  and I want it to run automatically when startup.
  
I tried using (&) and (&, disown) but this done via command line.
My actual Question is How to make this script run at start up and keep it in back ground??
  
  
Thank you.

---

### Post by nothingspecial on 2012-02-15
*Thread moved to **General Help**.*

---

### Post by aeiah on 2012-02-15
they're usually called daemons in unix-land, but i suppose they are also called services.

anyway, what you want is an init script:
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

although to be honest, im lazy and just run it either using my desktop environment's startup applications feature, or i add it to /etc/rc.local if i want it to run as root at boot.

---

### Post by SeijiSensei on 2012-02-15
> **aeiah said:**
> i add it to /etc/rc.local if i want it to run as root at boot.

^This.

You don't need to write an entire script either.  You can just put the commands directly into rc.local.

---

