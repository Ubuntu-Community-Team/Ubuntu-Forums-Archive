---
title: "Compiz animation add-ons dissapeared"
date: 2009-08-10
forum: General Help
---

### Post by TheNosh on 2009-08-10
i recently realized that my windows no longer go up in flames when i close them. i figured it was just that the option had been accidentally unselected. however when i went to reselect it in ccsm the entire animation add-ons plugin was not in the menu. i'm pretty sure that animation add-ons is part of "Compiz-fusion plugins main" package. so i purged that and reinstalled it (and i did the same with "Compiz-fusion plugins extra") but animation add-ons is still gone.

tl;dr: animation add-ons is not showing up as an option in ccsm, how do i get it back?

---

### Post by gettinoriginal on 2009-08-10
Try resetting the defaults (broom), then try the addons

---

### Post by TheNosh on 2009-08-10
> **gettinoriginal said:**
> Try resetting the defaults (broom), then try the addons

how do i use the  broom when "animation add-ons" doesn't appear in the menu at all?

---

### Post by TheNosh on 2009-08-12
bump

---

### Post by gettinoriginal on 2009-08-12
Sorry it took me so long to get back.  This will set set all of Comiz to default, so if you have numerous settings there, they will have to be reset:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
I am posting a screenshot of my synaptic, hoping that it might help find the missing app.
[ATTACH]124564[/ATTACH]
Sorry, don't have any other ideas, good luck  :P

---

### Post by Jeahavee on 2009-09-08
:popcorn: same problem here. I reloaded everything still didn't get it back.

---

### Post by TheNosh on 2009-09-08
> **Jeahavee said:**
> :popcorn: same problem here. I reloaded everything still didn't get it back.

yea, uninstalling/purging and reinstalling doesn't seem to help. luckily Compiz isn't really an important functional piece of the OS so it's not too big an issue.

also i'm planing on switching to Arch on the next weekend that i have any free time. best of luck to you in finding a solution though.

---

