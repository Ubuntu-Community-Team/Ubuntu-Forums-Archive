---
title: "gnome wouldn't start up after xmonad"
date: 2009-11-26
forum: General Help
---

### Post by pedrotuga on 2009-11-26
Ok, i've been disapointed with ubuntu's stability for the last few releases. Yet i am still using it :lolflag:

Anyway... today, another annoying problem popped up. I am kind of frustrated with having to move windows around and wanted to give a try to tiling window managers. So I installed xmonad and tried it out (way easier to use than one might expect). Ok, it was cool... but i connect to internet through wireless, whose profiles are managed by that thingy on gnome's notification area. So, yeah... no internet connection. Dealbreaker, i would google how to fix it, if i could just google (lame humor).

This was very anoying and I think it turns less experienced people away from ubuntu and free software in general.

Good news is: it's quite easy to fix, so here's quick way that should do it:

[COLOR="Red"]**1.**[/COLOR]Press Ctrl+Alt+F1 this will prompt you to login in a parallel session. You can open a few of them if you wish try out Ctrl+Alt+F2 Ctrl+Alt+F3, etc. Ctrl+Alt+F7 should take you to a X (i.e. graphical) session, which in your case is broken, that is why you're reading this.

[COLOR="Red"]**2.**[/COLOR]After logging with your username/password, type in:
```
sudo top|grep Xorg
```
and enter your passowrd

you'll see something like this

```
p@p-laptop:~$ sudo top|grep Xorg
 1572 root      20   0 36196  12m 7764 S    2  0.6   0:16.27 Xorg               
 1572 root      20   0 36176  12m 7740 S    0  0.6   0:16.28 Xorg               
 1572 root      20   0 36176  12m 7752 S    0  0.6   0:16.29 Xorg               
 1572 root      20   0 36172  12m 7752 S    1  0.6   0:16.31 Xorg               

```

it should print a new line every second or so.


[COLOR="Red"]**3.**[/COLOR]
The number in the beginning of the lines is the processid of Xorg windows server porces. In my case, the process we're looking for is 1752.
So.... hit Ctrl+c to stop top and type:
```
sudo kill -9 [process_number]
```, being  [process_number] the actual process id we checked on **[COLOR="Red"]3.[/COLOR]**.

**```
4.
```**Now we start Xorg again and for some esoteric reason it fixes it.
```
sudo startx
```


This is was kind of a second line on/off switch. Can't beat the efficiency of good low tech :)

It would be some nice reading if anybody could explain why does this hapens and why does restarting X fixes this while rebooting the computer does not.

---

### Post by bapoumba on 2009-11-28
Moved to General Help.

---

