---
title: "Gnome Panel problem"
date: 2010-07-09
forum: General Help
---

### Post by kridybel on 2010-07-09
Hello All, 

Since ubuntu 10.04 I have regularly but not always following panel problem:
on the righthand side of the top panel the "logon chooser" and the switch of button are not displayed. Usually a part of the items more on the left are copied on them again. Look at the attached picture.

How can this be resolved?
Thx a lot in advance.


[edit][solved]
seems to be solved by 10.04.1 update. Haven't seen the issue since then.

---

### Post by Devi1903 on 2010-07-09
Identical problem here. Any help would be much appreciated.

I had assumed this would be fixed with an update, as i have had it since i first installed the LTS the day it was released. But no update has solved it as of yet.

---

### Post by teonghan on 2010-07-18
Me three. Bet you all have nVidia card, huh? Because all the computers in my lab which has nVidia card has this similar problem too. Well, I like compiz very much but I got fed up and eventually turn it off. ~sigh~

Check these post out:
[http://ubuntuforums.org/showthread.php?t=1474932](http://ubuntuforums.org/showthread.php?t=1474932)
[http://ubuntuforums.org/showthread.php?t=1481030](http://ubuntuforums.org/showthread.php?t=1481030)

---

### Post by lidex on 2010-07-18
This may help:
[http://ubuntuforums.org/showpost.php?p=9570064&postcount=5]("http://ubuntuforums.org/showpost.php?p=9570064&postcount=5")

---

### Post by kridybel on 2010-07-25
> **teonghan said:**
> Me three. Bet you all have nVidia card, huh? Because all the computers in my lab which has nVidia card has this similar problem too. Well, I like compiz very much but I got fed up and eventually turn it off. ~sigh~

Check these post out:
[http://ubuntuforums.org/showthread.php?t=1474932](http://ubuntuforums.org/showthread.php?t=1474932)
[http://ubuntuforums.org/showthread.php?t=1481030](http://ubuntuforums.org/showthread.php?t=1481030)

Yes I do have an Nvidia card. Now I still have to check your and lidux' suggestions.

---

### Post by lidex on 2010-07-25
Or maybe a different theme?

---

### Post by kridybel on 2010-08-05
> **lidex said:**
> This may help:
[http://ubuntuforums.org/showpost.php?p=9570064&postcount=5]("http://ubuntuforums.org/showpost.php?p=9570064&postcount=5")


Thanks for the suggestion but this one is not persistent enough as today the old error appeared again.

---

### Post by zappal on 2010-12-24
oh comon!, this thread dies and marked as sloved, how is that so?
this dang problem i have been dealing with since 9.04, persisted with a fresh install of 10.04 and a fresh install of 10.10

Its really aggrivating, I cant beleive they have not fixed this. Its also happening on my wifes laptop. We are not using Nvidea, so that has nothing to do with it.

Resetting the panel helps, but then it eventually gets all messed up again.

I'm running the link from above, and if it happens again, Im ditching 10.10 and installing the beta and if the gnome 3 does it, ill have a heartattack.

---

### Post by lidex on 2010-12-24
> **zappal said:**
> oh comon!, this thread dies and marked as sloved, how is that so?
this dang problem i have been dealing with since 9.04, persisted with a fresh install of 10.04 and a fresh install of 10.10

Its really aggrivating, I cant beleive they have not fixed this. Its also happening on my wifes laptop. We are not using Nvidea, so that has nothing to do with it.

Resetting the panel helps, but then it eventually gets all messed up again.

I'm running the link from above, and if it happens again, Im ditching 10.10 and installing the beta and if the gnome 3 does it, ill have a heartattack.

It's a bug. Have a look here:
[https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-panel/+bug/439448)

One workaround seems to be killing gnome-panel (it will auto spawn):
```
killall gnome-panel
```

---

