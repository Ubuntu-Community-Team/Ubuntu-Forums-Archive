---
title: "Ubuntu 12.04 emerald and shutdown hang"
date: 2012-06-03
forum: General Help
---

### Post by jinjin on 2012-06-03
hi all, i've been using ubuntu for a while and my first one was 9.04 and i've been reluctant in upgrading for many reasons.  but recently, i upgraded to ubuntu 10.04 and not ubuntu 11.04 since ubuntu 11.04 had alot of thing i hated.   however, because alot of upgrades are not available to 10.04 anymore and since 12.04 came up, i decided to upgrade to 12.04, even though i knew there would be alot of things i'd from 12.04 since it retains things from 11.04.

man it was horrible, i hated the new unity and many other functions.  i quickly replaced it with gnome and tried to fix all the things i hated and put back what i loved about 10.04.  however, one of the things i could not fix was when i tried to get eremald themer, it's not available.   is emerald themer not supported on ubuntu 12.04?  it there anyway i can get it?
 if not there there any alternative way to customize windows borders and panes on ubuntu 12.04?
also , my ubuntu keeps hanging on a shutdown or restart, i have to manually hold the shutdown button, is any else experiencing and have a solution.

man is 12.04 alot of trouble, is it really worth it? worth the upgrade? i'm thinking of going back to 10.04, should i?

---

### Post by jinjin on 2012-06-04
bump

---

### Post by cariboo on 2012-06-04
Keep in mind that we are all volunteers here, it may take a while for someone that can answer your question to see it.

Common etiquette dictates that you shouldn't bump your post until at least 24 hours has elapsed.

---

### Post by jinjin on 2012-06-04
> **cariboo907 said:**
> Keep in mind that we are all volunteers here, it may take a while for someone that can answer your question to see it.

Common etiquette dictates that you shouldn't bump your post until at least 24 hours has elapsed.
sorry i didn't know about that, i'm fairly noob as u can see by my post counts

---

### Post by Zvlwab on 2012-06-04
> **jinjin said:**
> hi all, i've been using ubuntu for a while and my first one was 9.04 and i've been reluctant in upgrading for many reasons.  but recently, i upgraded to ubuntu 10.04 and not ubuntu 11.04 since ubuntu 11.04 had alot of thing i hated.   however, because alot of upgrades are not available to 10.04 anymore and since 12.04 came up, i decided to upgrade to 12.04, even though i knew there would be alot of things i'd from 12.04 since it retains things from 11.04.

man it was horrible, i hated the new unity and many other functions.  i quickly replaced it with gnome and tried to fix all the things i hated and put back what i loved about 10.04.  however, one of the things i could not fix was when i tried to get eremald themer, it's not available.   is emerald themer not supported on ubuntu 12.04?  it there anyway i can get it?
 if not there there any alternative way to customize windows borders and panes on ubuntu 12.04?
also , my ubuntu keeps hanging on a shutdown or restart, i have to manually hold the shutdown button, is any else experiencing and have a solution.

man is 12.04 alot of trouble, is it really worth it? worth the upgrade? i'm thinking of going back to 10.04, should i?


XFCE > Unity
I didn't want to upgrade from 10.04 either, because I hate the new Unity GUI. That's why I decided to upgrade to Xubuntu 12.04, which I like even better now than I liked Gnome2 back then.

Emerald
Follow this tutorial: [http://ubuntuforums.org/showthread.php?t=1754637](http://ubuntuforums.org/showthread.php?t=1754637)

Shutdown
There is a bug with the halt command. If you are using this command to shut down
```
sudo halt
```
you should instead use
```
sudo halt -p
```

Fresh install
I don't know wether you did a fresh install or an upgrade, but my personal experience is that a fresh install is mostly better than an upgrade.

---

