---
title: "plex help"
date: 2012-04-10
forum: General Help
---

### Post by hedoe on 2012-04-10
im running 11.10 64-bit and im trying to install plex
but when i use the
sudo gedit /ect/apt/sources.list
command i get a black window with no text or list in it
any ideas on how to fix this?
thanks

---

### Post by PhantomTurtle on 2012-04-10
Try,
```
gksudo gedit /etc/apt/sources.list
```
instead

---

### Post by hedoe on 2012-04-10
update
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1017_12_18.png[/IMG]

---

### Post by hedoe on 2012-04-10
so i did some exploratory surgery
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1017_22_49.png[/IMG]

[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1017_23_59.png[/IMG]

---

### Post by PhantomTurtle on 2012-04-10
Does the third picture you posted mean that it opens fine now. Try adding the line to etc/apt/sources.list.distUpgrade

EDIT: NWM, you spelled etc wrong from what I see in your screenshot, you wrote ECT, when it's supposed to be ETC.

So run,
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by hedoe on 2012-04-10
the wise turtle shows wisdom
thanks for the catch btw

but now im having another issue
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1019_12_09.png[/IMG]

---

### Post by PhantomTurtle on 2012-04-10
> **hedoe said:**
> the wise turtle shows wisdom
thanks for the catch btw

but now im having another issue
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1019_12_09.png[/IMG]

Well what's wrong with it(more details please)? Do you mean the errors in the terminal window? If so, then you can safely ignore them.

---

### Post by hedoe on 2012-04-10
yeah the error in the terminal is what i was refering to
but i should forge ahead anyway?

---

### Post by PhantomTurtle on 2012-04-10
> **hedoe said:**
> yeah the error in the terminal is what i was refering to
but i should forge ahead anyway?

Oh yeah that's fine, it's normal, just keep going.

---

### Post by miasmablk on 2012-04-10
could you please post your terminal/ gedit  outputs between /CODE tags these screen shots are difficult are to read.

---

