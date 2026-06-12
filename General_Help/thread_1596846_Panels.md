---
title: "Panels"
date: 2010-10-14
forum: General Help
---

### Post by Goolie on 2010-10-14
Okay, so this is a little weird, and I'm a little dumb.  I've tried googling the problem but I've found that either I'm not searching correctly, or there isn't a way to do what I'm trying to do.

Basically, I lost the panel on the top of my screen.  Now, I'm pretty sure there has got to be a command line way to open up the Panels preferences, or make them come back to me.  It disappeared after a failed upgrade to 10.10 (it just closed out saying it couldn't do it because apt-get was locked [i was installing something, der])

Anyway, how to get it back?  Or at least get into the preferences window for my panels?  Or if nothing else, the configuration files where I can change these things.

Thanks,

Goolie.

---

### Post by gandaran on 2010-10-14
if you click the bottom panel and choose new panel doesn't it work?
you can also click on properties and move the bottom panel to the top.

---

### Post by nothingspecial on 2010-10-14
If you still have the bottom panel, simply right click on it and choose "new panel".

---

### Post by Goolie on 2010-10-14
Sorry, I don't have either, I manually removed the bottom panel a long time ago.

---

### Post by nothingspecial on 2010-10-14
How did you remove it?

I have no panels.

---

### Post by ritusrivastava on 2010-10-14
Try this:
1. In the terminal window, type the following in the order:
1. gconftool-2 --shutdown
2. rm -rf ~/.gconf/apps/panel
3. pkill gnome-panel

Hope that helps
-Ritu

---

### Post by WorMzy on 2010-10-14
You can reset the panel configuration to default by opening a terminal and running:

```
gconftool-2 --shutdown
rm -r ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Goolie on 2010-10-14
I did those commands and tried logging in and out after and tried again and shut-down and restarted as well.  

They didn't work.

O.o

---

### Post by WorMzy on 2010-10-14
Odd. You are using Ubuntu, right? Not kubuntu or some other variant?

What happens if you run
```
gnome-panel
```
in a terminal?

Any error codes?

---

### Post by Goolie on 2010-10-14
> **WorMzy said:**
> Odd. You are using Ubuntu, right? Not kubuntu or some other variant?

What happens if you run
```
gnome-panel
```in a terminal?

Any error codes?

Ubuntu 10.04 and:

Nope, no error codes, but it brought my panels back!  Top and bottom!

You sir, are my hero.

---

### Post by WorMzy on 2010-10-14
Don't celebrate too soon, that'll only last for the rest of your session (or until you close the terminal/end the process), but at least we know that the problem is just that gnome-panel isn't being started, and not something more serious like a broken package.

You have three options:
[LIST=1]
[*]Manually run gnome-panel every time you log in (Alt+F2 would be better than a terminal if you choose this option)
[*]Create a startup applications entry for gnome-panel
[*]Edit your gconf settings to set gnome-panel as your default panel
[/LIST]

[LIST=1]
[*]is pretty self obvious
[*]is quite simple - just open the Startup Applications list (System -> Preferences -> Startup Applications _OR_ Alt+F2, gnome-session-properties, run) and add a new entry that has "gnome-panel" as it's command
[*]isn't difficult either, just run gconf-editor and browser to /desktop/gnome/session/required_components and set "panel" to "gnome-panel". If it's already set to that, or you don't want to change it, then use option 1) or 2).
[/LIST]

---

