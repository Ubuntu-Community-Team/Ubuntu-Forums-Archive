---
title: "Gnome hangs up when creating LVM snapshot"
date: 2010-08-14
forum: General Help
---

### Post by poisonborz on 2010-08-14
Hola,
Recently, I've tried to create a snapshot of my /root folder in 10.04 (I remember to have done so a couple of times without trouble).

I used the command
[HTML]
lvcreate -L10G -s -n rootsnapshot /dev/server/root[/HTML]

Without a hint of HDD activity, Gnome (?) hangs up - I can move the mouse, and the clock is moving on, but I can't click on anything. No HDD activity, and this goes on forever (after a while, the whole system locks up). This happens each time when I try to create a snapshot.

What could be the problem?

---

