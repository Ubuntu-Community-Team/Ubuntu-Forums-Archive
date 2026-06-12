---
title: "Running Nautilus wouthout Terminal"
date: 2009-09-20
forum: General Help
---

### Post by MacGoose on 2009-09-20
Hi!

Is it possible to run Nautilus as root without the Terminal also running?  I've set up a launcher to run the Terminal with the gksudo nautilus command so I don't have to do anything in the Terminal - making at least that one easier.  But now since I really don't need the Terminal window for anything I would very much like to free up the panel.

, MacGoose

---

### Post by AmerNewbieInDE on 2009-09-20
try alt+f2, type gksu nautilus or gksudo nautilus

---

### Post by sunchiqua on 2009-09-20
```
gksudo nautilus / &

```Terminal should disappear right after the appearance of Nautilus.

---

### Post by drs305 on 2009-09-20
This is *not* an elegant solution, but it will work (preferably if you don't have or want any other terminals open) if you feel the need to use the terminal. It will work for any command you want opened in terminal but then run without the terminal remaining open.

Add this to the end of whatever command you are using to open nautilus in a terminal:
> 
& sleep 3 && killall gnome-terminal

It will sleep for 10 seconds, giving you time to enter your password if necessary, then kill any open terminal - *including any others you might want to keep open*. The full command would be something like:
```

gksu nautilus & sleep 10 && killall gnome-terminal

```

It's not a great solution, but it will work until someone posts a better one.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Penguin Guy on 2009-09-20
> I've set up a launcher to run the Terminal with the gksudo nautilus command
Why not just get the launcher to run the command [COLOR="Green"]gksu nautilus /[/COLOR]? That works fine for me.

---

### Post by MacGoose on 2009-09-20
Thanx but none of the solutions above work.  Except for maybe the sleep and kill command but it's prone to unwanted actions so I'll leave it alone.

Anyway.  Tried the actions above and they all open Nautilus but still leave the Terminal window open and on the panel...

, MacGoose

---

### Post by Keith Hedger on 2009-09-20
place this:```
#!/bin/sh

DIRNAME=$(echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g')
FILENAME=$1

if [ ! -d "$DIRNAME/$FILENAME" ];then
	FILENAME=""
fi

foo=$(gksudo -u root -k -m "Enter Your Admin Password" /bin/echo "got r00t?")
sudo nautilus --no-desktop "$DIRNAME/$FILENAME"

```
in a file called "Root Nautilus Here" in ~/.gnome2/nautilus-scripts make it executable, then right click a folder in nautilus and select Scripts->Root Nautilus Here to open a root nautilus at that place

---

### Post by Bonster on 2009-09-20
install the nautilus-gksu plugin

---

### Post by t0p on 2009-09-20
> **MacGoose said:**
> 
Anyway.  Tried the actions above and they all open Nautilus but still leave the Terminal window open and on the panel...


How very odd!  AmerNewbieInDE advised you to hit **Alt+F2** and type into the box 

```
gksudo nautlilus
```

I do that an awful lot, and you don't even need to open a terminal to do it, so I don't understand what you mean when you say it leaves a terminal window open.  What terminal window?  Why did you open a terminal window? Please explain.

---

### Post by The Cog on 2009-09-20
When you create a launcher, you have a choice of application type - Application, Application in terminal, or Location. Choose Application and put the command **gksu nautilus** in there.

---

### Post by Tipped OuT on 2009-09-20
> **MacGoose said:**
> Thanx but none of the solutions above work.  Except for maybe the sleep and kill command but it's prone to unwanted actions so I'll leave it alone.

Anyway.  Tried the actions above and they all open Nautilus but still leave the Terminal window open and on the panel...

, MacGoose

> **The Cog said:**
> When you create a launcher, you have a choice of application type - Application, Application in terminal, or Location. Choose Application and put the command **gksu nautilus** in there.

Yes, as "The Cog" said... all you have to do is press ALT + F2 at the same time. A little window should pop up, then you type "gksudo nautlilus" in the run box, and you're good to go.

---

### Post by MacGoose on 2009-09-20
> **t0p said:**
> How very odd!  AmerNewbieInDE advised you to hit **Alt+F2** and type into the box
The thing was that I really didn't want to type anything - except for a password, of course.

[quote=The Cog]When you create a launcher, you have a choice of application type - Application, Application in terminal, or Location. Choose Application and put the command **gksu nautilus** in there.[/quote]
Thanx!  That was it.  Just Application, not Application in Terminal...

, MacGoose

---

### Post by CatKiller on 2009-09-21
> **MacGoose said:**
> The thing was that I really didn't want to type anything - except for a password, of course.

Meh. It does remember what you've typed, so you only need to press down a couple of times to get a command that you might run often, such as *gksudo nautilus*, or *gconf-editor*, or whatever.

Glad you got your launcher working, anyway.

---

