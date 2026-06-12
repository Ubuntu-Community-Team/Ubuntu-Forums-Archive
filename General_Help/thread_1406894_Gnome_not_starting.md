---
title: "Gnome not starting"
date: 2010-02-14
forum: General Help
---

### Post by bigred1 on 2010-02-14
When I restart my system, it never gets to Gnome. It give an error message for a few seconds "Install problem: The configuration details for Gnome power manager..."  then loads up Vuze correctly, but never loads Gnome. (The problem is not the power manager; that is just the one error message that makes its way to the screen.)

If I close Vuze, I just get a black screen and a cursor-clock.

I guessed that there might be a problem with grub and kernel versions. However ls /boot shows that the latest kernel there is 2.6-31-17-generic; I change menu.lst to use that one instead of 2.6-31-14, and the same bug occurs just as before.

Any ideas how I can figure this one out?

---

