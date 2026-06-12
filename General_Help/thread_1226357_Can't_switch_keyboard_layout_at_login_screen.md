---
title: "Can't switch keyboard layout at login screen"
date: 2009-07-29
forum: General Help
---

### Post by approaching on 2009-07-29
There are a lot of posts about this in the past, but none of them seem to be fixed properly (or all that recent), most just say to install with one keyboard layout (which is the one that will be used for the log in screen), and use another once you are logged in. There has to be a way to be able to select which layout you want at the log on screen. In my scenario I use the Dvorak layout, and my girlfriend uses QWERTY. I can make it switch once I log in, but is there any way to make a global option to switch that I can use before a user has logged in?

---

### Post by credobyte on 2009-07-29
```
 
gconftool-2 --type string --set /desktop/gnome/peripherals/keyboard/kbd/layout "layout name"

```
 
Use [COLOR=darkred]$USER[/COLOR] to determinate, who's logged in & change the layout to whatever you need ( bash, startup ) ;)

---

### Post by approaching on 2009-07-29
I'm sorry, but I don't know if I either didn't understand your instructions, or what, but I entered that command, and I don't believe that I got anything.
```

gconftool-2 --type string --set /desktop/gnome/peripherals/keyboard/kbd/layout "us"

```

That is the layout I would like to add, but I also want to be able to switch to the dvorak layout.

and I have no environment variable or program called ($)USER

---

### Post by credobyte on 2009-07-29
No, you have it:
```
dainis@ubuntu:~$ echo $USER
dainis

```

As per gconf tool, add 2 layouts and try switching between them by using the command I posted previously.

---

### Post by approaching on 2009-07-30
This may seem like a bit of a cop out, but I was sort of confused as to what I was supposed to do. So, after some poking around, I found out that Karmic Koala was going to implement just what I was looking for, a drop down box on the log on page with the keyboard layouts in it. The graphics are a little buggy at the moment, but it seems to work just fine for what I wanted.

---

