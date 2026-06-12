---
title: "Change a gconf-editor setting using CLI"
date: 2010-11-16
forum: General Help
---

### Post by lsutiger on 2010-11-16
I upgraded to 10.04 today for a NX server. I exported the old users to the new server. On the old server I used ubuntu-tweak to lock down a lot of actions for all of the users except one. All of the user's settings carried over also. I can no longer run a terminal on a user's account (This is on purpose!)
All I am wanting to do is change the theme and move the min,max,close buttons to the right of the window (because this will drive the users insane).
I can ssh into the server and change the setting that way, but I have no idea what to change.
So, what setting do I need to change?

Thanx!

---

### Post by lsutiger on 2010-11-16
Solved!
Used gconftool-2 with less to find the key and changed it!

---

### Post by amrun on 2011-02-02
could you show how you found the key? tried it myself but getting nowhere.. :S

---

### Post by lsutiger on 2011-02-03
I'd have to go do some research to find out exactly what I did...I do know that I found the answer via google. Try googling gconftool-2...I used less to find the key I was looking for within the gconf file (which I forgot exactly what it is named).

---

### Post by wojox on 2011-02-03
I happen to have this:

```
sudo gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close" 
```

---

