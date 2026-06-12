---
title: "Help setting a rule in UFW/Iptables"
date: 2009-09-30
forum: General Help
---

### Post by viking_maniac on 2009-09-30
[COLOR=black][FONT=Verdana]I want to set a rule in the firewall that blocks one outgoing port, and it needs to block that port regardless of software that tries to use it on the internet.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I'm not so familiar with Ubuntu's firewall, so suggestions would be appreciated! :)[/FONT][/COLOR]

---

### Post by Enigmapond on 2009-09-30
An easy way to do that is to install Firestarter which is a frontend application for the firewall. Very easy to block/allow ports. If not, 
```
sudo ufw deny *port#*
```

---

### Post by credobyte on 2009-09-30
Here's a tutorial on how to use it ( allowing|denying ports|ip's, etc. ): [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by XCan on 2009-09-30
I do not believe UFW can help you to block outgoing traffic. Thus you'll have to rely on something else, configure iptables manually, firestarter, or perhaps Guarddog. I think firestarter is the simplest alternative in this case.

---

### Post by viking_maniac on 2009-10-01
I tried Firestarter from the Package Manager, but I uninstalled it.

Has it messed up my UFW settings?

This is the status:
```

$ sudo ufw status verbose numbered

Status: active
Logging: off
Default: deny
New profiles: skip
``````
$ sudo ufw app list

Available applications:
  CUPS
```

Thanks!

---

### Post by XCan on 2009-10-01
Maybe, maybe not, depends on if it cleared its rules from iptables or not. It would be much more informative if you pasted the output of ```
 iptables -L 
``` But as I said, I don't think you can block outgoing with UFW.

---

