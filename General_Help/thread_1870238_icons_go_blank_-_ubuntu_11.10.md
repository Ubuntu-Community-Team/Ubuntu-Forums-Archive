---
title: "icons go blank - ubuntu 11.10"
date: 2011-10-26
forum: General Help
---

### Post by ccxzy on 2011-10-26
Hi,

I installed ubuntu 11.10 2 days ago, recently I'm having these blank icons in nautilus (also desktop).

[[IMG]http://img823.imageshack.us/img823/9646/sscn.th.png[/IMG]](http://imageshack.us/photo/my-images/823/sscn.png/)

I don't know if it's related but I installed deluge and vlc before this becomes recurring, and vlc was running everytime it occurs. (but it does not occur at the same time vlc starts, it occurs after 15 minutes or so; but again, I don't know if it's related)

can anyone help me out?

the icons are restored after restart, but it occurs again after 10-20 min.

---

### Post by razaz03 on 2011-10-26
> **ccxzy said:**
> Hi,

I installed ubuntu 11.10 2 days ago, recently I'm having these blank icons in nautilus (also desktop).

[[IMG]http://img823.imageshack.us/img823/9646/sscn.th.png[/IMG]]("http://imageshack.us/photo/my-images/823/sscn.png/")

I don't know if it's related but I installed deluge and vlc before this becomes recurring, and vlc was running everytime it occurs. (but it does not occur at the same time vlc starts, it occurs after 15 minutes or so; but again, I don't know if it's related)

can anyone help me out?

the icons are restored after restart, but it occurs again after 10-20 min.

Did you install ccsm and any of its plugins? I just got this problem when reverting to gnome-fallback and installing ccsm with it's fusion extra plugin. I think one of those is the cause of your problems. It's not stable for me and I detest unity so I'm in the process of deciding Kubuntu Xubuntu or Mint.

Sorry I couldn't be of more help- try using Unity or removing ccsm if those suggestions are relevant.

raz

---

### Post by oldtimer7777 on 2011-10-26
I tried for a small time today to play with composite manager and compiz and getting it to run like it did in previous releases of Ubuntu, but I was not successful in this attempt... I've been playing with Linux for a while, a long while, and if I can't easily get it running, goodluck anyone else getting it to run either..  I should just be able to go into Appearance and then click "Extra Effects" and reboot.  Poof. Done. But no.

> **razaz03 said:**
> Did you install ccsm and any of its plugins? I just got this problem when reverting to gnome-fallback and installing ccsm with it's fusion extra plugin. I think one of those is the cause of your problems. It's not stable for me and I detest unity so I'm in the process of deciding Kubuntu Xubuntu or Mint.

Sorry I couldn't be of more help- try using Unity or removing ccsm if those suggestions are relevant.

raz

---

### Post by ccxzy on 2011-10-26
oh, but i haven't installed ccsm and I'm still using unity.

I wonder where this comes from :/

---

### Post by ccxzy on 2011-10-27
I got the blank icons again, and that's after closing opera. Last time I got it after minimizing opera. (but the bug is not recreated all the time)

As I see, after closing/minimizing opera, somehow ubuntu wants to refresh the appearance of the icons/ desktop?? but after refreshing, it loads blank icons.

The problem may not be opera though, that's just what I observe.

---

### Post by sroecker on 2011-10-27
I seem to have a similar problem since today.
Yesterday my desktop looked normal, since today nautilus on one computer looks like yours.
(On the other computer the gnome icon set is used)
Also my gtk theme is set to a gray one instead of Ambiant.

I already downgraded some packages but haven't found the right one.
Do you have oneiric-proposed enabled?

---

### Post by Frogs Hair on 2011-10-27
A Temporary fix in most cases is the command below .```
nautilus -q
```

See the section on Nautilus crashing at the link .[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by sroecker on 2011-10-27
Related Bugs:
[http://launchpad.net/bugs/881263](http://launchpad.net/bugs/881263)
[http://launchpad.net/bugs/879793](http://launchpad.net/bugs/879793)
[http://launchpad.net/bugs/859723](http://launchpad.net/bugs/859723)[URL="http://ubuntuforums.org/http//launchpad.net/bugs/859723"]
[/URL]

---

### Post by ccxzy on 2011-10-27
I have not installed oneiric-proposed.

thanks sroecker! from your post about bug reports, it is now clear that in my case, the opera is the culprit. :)

---

### Post by Arwen17evenstar on 2011-11-07
I have the same problem and it happened completely randomly. Restarting several times did not fix it.

nautilus -q fixed it. Thank you.

---

