---
title: "How do I do this?"
date: 2009-12-10
forum: General Help
---

### Post by pepsifx357 on 2009-12-10
How to you start a program from the command line, or more specifically a luancher on the desktop, so that it starts on a certain workspace.

Like Ardour start on workspace 3, something like that.

Thanks,

Ben

---

### Post by hwttdz on 2009-12-10
I think wmctrl can do what you want.  

Your launcher might look something like
program_being_launched; wmctrl -r "program_being_launched" -t1

Of course say the program is notepad or something, and you already have some open, then it might move all of them.  I'm not sure.

---

### Post by whitethorn on 2009-12-10
This depends on if you're using compiz or metacity.  So either with desktop effects or without.  With you need to use the plugin Viewport switcher or Place window.  Without desktop effects you need to use devilspie, it's a small program that runs in the background and lets you do alot of stuff with windows.  

```
sudo apt-get update && sudo apt-get install devilspie
```

There are a bunch of guides out there for configuring devilspie.

---

### Post by hwttdz on 2009-12-10
whitethorn, how would one do this in compiz? I looked for the option but didn't see it.

Edit: I think it's place windows plugin in compiz, then fixed window placement, and then windows with fixed viewport.  
Does that mean that you can't move it from that viewport if you want to? If so maybe wmctrl or devilspie would be a better solution, because then it just launches there and resides wherever you want.

---

### Post by blackened on 2009-12-10
> **hwttdz said:**
> ...Does that mean that you can't move it from that viewport if you want to?...

Using the Fixed Viewport option of the Place plugin will start the window in the viewport of your choosing. After that you can move that program to any other viewport at your leisure. If you were to close and reopen the program, then it would again start in the viewport you specified.

---

### Post by pepsifx357 on 2009-12-11
The reason I was wanting to do this is so that I could click one launcher and it would open up all of the apps I need in their respective windows.

---

### Post by hwttdz on 2009-12-11
Makes perfect sense why one would want to do that and it should be quite doable with the tools outlined.  Other options include saving your session as you logout (I think I like this one best, this is more or less designed to do exactly what you ask).  If you run gnome-session-properties and then check "Automatically remember running applications when logging out", when you log back in gnome will restore your workspaces to more or less how they were.  xfce has a similar option, and I would assume kde does as well.  Another option might be to use the hibernate function instead of shutting down.

---

### Post by pepsifx357 on 2009-12-11
I was trying to do this with wmctrl and ardour, what would be the command to put this application on desktop 3?  It doesn't seem to have a help file.

---

### Post by guriinii on 2009-12-11
you can do this in devilspie and set it to launch on boot.
 
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

also this may be of use:

[http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie](http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie)

---

### Post by falconindy on 2009-12-11
> **pepsifx357 said:**
> I was trying to do this with wmctrl and ardour, what would be the command to put this application on desktop 3?  **It doesn't seem to have a help file**.
It certainly does have a man page.

[http://pwet.fr/man/linux/commandes/wmctrl](http://pwet.fr/man/linux/commandes/wmctrl)

---

### Post by hwttdz on 2009-12-11
pepsifx357, in general when you don't know how to use a program you can just type man programname at the terminal and it will give you all sorts of useful info, oftentimes including a few examples.  Further the developer oftentimes posts useful information as in this case [http://tripie.sweb.cz/utils/wmctrl/](http://tripie.sweb.cz/utils/wmctrl/) (found by googling wmctrl). If you're still having trouble post the command that you're trying to use, along with what you expect it to do and what it actually does (including any error output), and perhaps someone will be able to help you.

---

### Post by pepsifx357 on 2009-12-11
Thanks guys, I thought it was usually --help.

---

