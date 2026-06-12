---
title: "Dapper Drake - Nothing Appears After Login - Orange/Red Screen"
date: 2006-06-01
forum: General Help
---

### Post by nowhere.inc on 2006-06-01
I'm hoping someone can help me with this it is driving me crazy! I just did a clean install of Dapper (for reference, everything with Breezy Badger worked great) and everything seems to work fine until I have to log in. I go to log in and it screen looks fine, but when I put in my username and password it takes me to a orange/red/brownish screen and nothing happens. It just stalls. Is the GUI not loading? I have an ATI Radeon 9000 and its an old HP computer. I wouldnt think it was a vid card problem because the login screen renders beautifully and if I login in terminal FAILSAFE mode a clean window pops up telling me how to use the terminal. I cannot get to the desktop. Any idea! Thanks so much I am going crazy!!

:-k

---

### Post by nanotube on 2006-06-01
well,it seems like it's not a video problem... but it doesn't hurt to try changing your driver to vesa, and seeing if that works. 
give it a whirl (unless someone comes up with better suggestion)

---

### Post by ozorba on 2006-06-01
Try Ctrl-Alt-F1 and login.
Rename .gnome directory, and all the files that start with .gtk...
Ctrl-Alt-F7 and try to login again.

---

### Post by Trab on 2006-06-01
ive had this issue before as well.
for me it was a gnome-loading issue.
have you tried just leaving it on that screen for about 20 minutes? then gnome loaded for me, and i was able to fix the error....
you could also try booking in recovery mode, when you get to the console, type
```

startx

```
and when that is up, click on one of the terminals, and type
```

gnome-session

```

this is just a temporary solution to help troubleshoot the problem.
-Trab

---

### Post by nowhere.inc on 2006-06-01
ok when I did "startx" it flashed a login thing that said "nautilus" and then went to a wavy background and that was it. Hmm.... Also, how to I change to vesa? Just edit xorg.conf and change Driver to "vesa"? Thanks so much yall!

---

### Post by nowhere.inc on 2006-06-01
sorry to bump this but I'm still not having any luck. thanks!

---

### Post by nanotube on 2006-06-03
[QUOTE=nowhere.inc]sorry to bump this but I'm still not having any luck. thanks![/QUOTE]
yes, just edit xorg.conf
there is a tutorial for that here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#If_you_used_the_default_install](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#If_you_used_the_default_install)

you could also try what others suggested, from another console, do
mv .gnome2 .gnome2-backup
and try restarting gnome.

---

### Post by FeANoR67 on 2006-10-30
> **nanotube said:**
> yes, just edit xorg.conf
there is a tutorial for that here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#If_you_used_the_default_install](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#If_you_used_the_default_install)

you could also try what others suggested, from another console, do
mv .gnome2 .gnome2-backup
and try restarting gnome.
i have the same problem and i waited more than one hour..
but the screen did not changed..and writing mv .gnome2 .gnome2-backup did not work also..i am using ubntu dapper..

---

