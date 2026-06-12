---
title: "Network reboot"
date: 2006-05-04
forum: General Help
---

### Post by woofcat on 2006-05-04
Every so often my network connections freak out and quit and i can accept this. It has happened with all my OS's (router going south) To solve this problem i have to reboot my Machine. Is there anyway with commands that i could get the same effect as rebooting my machine with out.. well you know rebooting my machine.

Any help would be great.

---

### Post by Qrk on 2006-05-04
I've always used this command, but it isn't exactly the same thing:

```
sudo dhclient
```

---

### Post by woofcat on 2006-05-04
[QUOTE=Qrk]```
sudo dhclient
```[/QUOTE]
Thanks, I'll give it a try next time things go sour.

---

### Post by Balut on 2006-05-04
try

sudo /etc/init.d/networking restart

---

