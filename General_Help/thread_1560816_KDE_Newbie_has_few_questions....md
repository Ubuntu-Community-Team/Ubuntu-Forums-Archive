---
title: "KDE Newbie has few questions..."
date: 2010-08-25
forum: General Help
---

### Post by vickoxy on 2010-08-25
Hi,
i am one gnome-user, but need to set up kde/Kubuntu/Mint 9 KDE on my wifes computer. So, i have few questions:

1) how to make kde not to start/memorize previous session after reboot?
2) in gnome-power-manager i can read Battery Health (mAh, Design Capacity...)-something like that in KDE? In KDE Power manager i have no such readings.
3) is there some cleaning tool as for gnome ubuntu-tweak?

---

### Post by dabl on 2010-08-25
I'm away from my Kubuntu system at the moment, but if you go into System Settings > Sessions, I believe you will find a tick box to choose whether you want to resume the prior session or open with a new session.

There's a "widget" for battery status -- click the "cashew" in the upper right corner, choose "unlock widgets", choose "Add widget", and scroll the the one want.  Once you have selected it and installed it, don't forget to "lock widgets" again.

Also, you can get help with Kubuntu here:  [http://www.kubuntuforums.net/index.php](http://www.kubuntuforums.net/index.php)

---

### Post by vickoxy on 2010-08-25
Thanks-found session options. But the battery icon/apple is showing only percentage. In gnome power-manager i have all battery relevant infos (battery health, designed power in mAh...)

---

### Post by vickoxy on 2010-08-26
push...

---

### Post by vickoxy on 2010-08-26
push...

3) is there some cleaning tool as for gnome ubuntu-tweak?

---

### Post by bergfly on 2010-08-28
Not aware of ubuntu tweak type app for KDE, however KDE out the box is a lot more configurable than gnome out the box, so maybe there is not as much need.

As far as the battery goes, sadly there is nothing better than the battery monitor plasmoid that I am aware of. 

You can of course pull it off the actual file, either

```
nano /proc/acpi/battery/BAT0/state
```
or 
```
nano /proc/acpi/battery/BAT0/info
```

depending on what you are looking for. Not pretty or flash and certainly not part of KDE, but all the info is there. 

Wish I could give better answers. Maybe there is some stuff on kde-look.org or kde-apps.org

---

