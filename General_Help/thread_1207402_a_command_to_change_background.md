---
title: "a command to change background"
date: 2009-07-08
forum: General Help
---

### Post by 10ghost on 2009-07-08
hi readers,
I just want to play around the /etc/cron.hourly
I want to change the wallpaper of my system hourly.
I need the command  to change background.

---

### Post by chriskin on 2009-07-08
if i may propose a workaround, as i do not know the command, the wallpaper-tray applet has this option.

you might want to check it

---

### Post by nothingspecial on 2009-07-08
Or you could try [[COLOR="Magenta"]drapes[/COLOR]]("http://freshmeat.net/projects/drapes/")

---

### Post by chriskin on 2009-07-08
> **nothingspecial said:**
> Or you could try [[COLOR=Magenta]drapes[/COLOR]]("http://freshmeat.net/projects/drapes/")

drapes doesn't work on my 9.04

---

### Post by 3rdalbum on 2009-07-08
The wallpaper is set by a Gconf key, so you can use gconftool to change it:

```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename '/home/chris/Possible Desktop Images/subu copy.png'
```

Obviously, you want to change the file path to the filepath of your desktop picture :-)

If you need more information, see *man gconftool-2*

---

### Post by 10ghost on 2009-07-08
how do i install desktop drape on my system then?

---

### Post by 10ghost on 2009-07-08
i just installed drape using the synaptic manager but realized that it gave me an error when trying to add to panel. the error was

[COLOR="Navy"][FONT="Courier New"]The panel encountered a problem "OAFIID:Drapes applet". 
DO you want to delete the applet from your configuration?[/FONT][/COLOR]

On clicking the option yes nothing happened the same was the case when i clicked no.
What could be the problem ?

---

