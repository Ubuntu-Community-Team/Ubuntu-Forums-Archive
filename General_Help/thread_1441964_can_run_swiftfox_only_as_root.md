---
title: "can run swiftfox only as root"
date: 2010-03-29
forum: General Help
---

### Post by k94382 on 2010-03-29
I installed fluxbox on an Ubuntu 9.10 server installation and then I installed swiftfox.
I used to be able to run swiftfox as a regular user but now swiftfox only starts when I type in a terminal

> sudo swiftfox

Can someone please tell me how I can run swiftfox as a regular user again?
By the way, I also get this problem with firefox.

---

### Post by lovinglinux on 2010-03-29
NEVER run Firefox or Swiftfox with sudo. You need to [fix permission issues](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2).

See [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by blazemore on 2010-03-29
Slightly less generic answer:

What happens if you try and run swiftfox from a terminal, not as root.

---

### Post by lovinglinux on 2010-03-29
> **blazemore said:**
> Slightly less generic answer:

What happens if you try and run swiftfox from a terminal, not as root.

At this point, since the OP already started it as sudo, it will get all sorts of problems, if it starts at all.

---

### Post by blazemore on 2010-03-29
Not at all. try
```
swiftfox --profilemanager
```

Make a new profile and set it as default.

Failing that,
```
sudo aptitude purge swiftfox && sudo apt-get install swiftfox
``` (if you installed from PPA)

---

### Post by k94382 on 2010-03-29
> **lovinglinux said:**
> NEVER run Firefox or Swiftfox with sudo. You need to [fix permission issues](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2).

See [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

That solved the problem. Thank you and thanks to everyone else who tried.

---

