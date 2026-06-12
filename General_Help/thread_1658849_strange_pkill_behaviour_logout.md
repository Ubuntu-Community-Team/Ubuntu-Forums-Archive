---
title: "strange pkill behaviour: logout"
date: 2011-01-03
forum: General Help
---

### Post by kimyoungil on 2011-01-03
For studies I've written some simulations. But there's an odd thing, when I try to kill the simulation I type:
sudo pkill sim
(sudo isn't really needed, but it shouldn't matter)

Whenever I do that I immediately logout, without any warning whatsoever. Is this normal :confused:

for other programs this works normally:
sudo pkill firefox
just kills firefox etc etc.


Even if the simulation isn't running, it still quits. But:
```
ik@heerlijkheid:~$ sudo ps -A | grep sim
13498 ?        00:00:00 gdm-simple-slav
```
so there's no important process that's getting killed I'd say.

What is happening here? :confused:
what's the effect of "sudo pkill sim" on other computers?

---

### Post by TeoBigusGeekus on 2011-01-03
pkill kills processes that match a pattern.
pkill sim kills your gdm session, that's why you are logged out.
Instead of pkill, use killall, which doesn't search for patterns but matches the input name exactly.

---

