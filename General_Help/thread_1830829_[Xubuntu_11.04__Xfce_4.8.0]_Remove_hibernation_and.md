---
title: "[Xubuntu 11.04 / Xfce 4.8.0] Remove hibernation and suspend options from menu?"
date: 2011-08-22
forum: General Help
---

### Post by The_Bonehunter on 2011-08-22
Dear community,

After searching the web and this forum, I found plenty of options for Ubuntu/Kubuntu with Gnome/KDE, but I could not find a solution for Xubuntu/Xfce.

My problem:

On an old Packard Bell laptop, both the hibernate and suspend options generate freezes and hard resets. As I am setting this laptop up for a new Linux user with hardly any computer experience, it would be nice to disable/hide these options to avoid frustration and computer avoidance.

Thus, is there anyway to disable or hide suspend and hibernate on Xubuntu 11.04 / Xfce 4.8.0? 

I tried this (found on web):

```
xfconf-query -c xfce4-session -np '/shutdown/ShowSuspend' -t 'bool' -s 'false'

xfconf-query -c xfce4-session -np '/shutdown/ShowHibernate' -t 'bool' -s 'false' 
```

Checked with xfconf, entries were added, but it had no effect.

Anyone?

---

### Post by Toz on 2011-08-23
Post #17 from [http://forum.xfce.org/viewtopic.php?id=4781]("http://forum.xfce.org/viewtopic.php?id=4781") worked for me on 11.04/4.8. Specifically, the second command:
```
xfconf-query -c xfce4-session -p /shutdown/ShowSuspend --create --set false --type bool
```
since I didn't have the entry yet in xfconf.

---

