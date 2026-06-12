---
title: "&quot;The following packages have been kept back:&quot; totem"
date: 2006-05-08
forum: General Help
---

### Post by mygravity on 2006-05-08
Hi,

Over the past month when my system's packages have been updated the following message is always displayed at the end:

```
The following packages have been kept back:
  totem
```

I have tried running 
```
sudo apt-get dist-upgrade
sudo apt-get upgrade
```

which both return the same message above regarding totem.

While this issue isn't causing any problems as totem still works fine, I'm curious as to what causes this situationa and whether it can be resolved.

Many thanks

Andrew

---

### Post by louis_nichols on 2006-05-08
Perhaps you set synaptic to lock to one version. Check totem under synaptic and then see if, under menu "package" you have "locked" checked

---

### Post by mygravity on 2006-05-08
Hi 

Have looked in Synaptic under Package and "Lock Version" is not set.

Here is what Synaptic looks like for the totem related files:
[[IMG]http://img347.imageshack.us/img347/473/screenshot7gv.th.png[/IMG]](http://img347.imageshack.us/my.php?image=screenshot7gv.png)

Thanks for the reply.

Andrew

---

### Post by louis_nichols on 2006-05-08
Well... I did a quick google, cause I was intrigued, and I think [this link]("http://www.debian-administration.org/articles/69") should help you.

---

