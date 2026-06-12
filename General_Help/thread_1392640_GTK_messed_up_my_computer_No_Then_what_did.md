---
title: "GTK messed up my computer? No? Then what did?"
date: 2010-01-28
forum: General Help
---

### Post by bobbuilder67 on 2010-01-28
Hello everybody,
I've only been using linux for about 6-8 months so forgive my newbie-ness, if this is an easy problem to solve.  Anyway I'll start from the beginning.

We and my family were using linux smashingly.  Everything worked great, and I loved it.  But a few days ago (on a quest for the perfect GUI programming in c++) I stumbled across the GTK C++ libraries.  It looked good, so I downloaded and installed:

1) pango
2) atk
3) cairo, and
4) gtk itself.

I programmed for about 30 minutes with GTK (It worked great).  Then I turned off the computer and headed off to school.  When I came back, everything was messed up:

1) the theme : Human-clearlooks was missing.
2) all the themes were missing, except for one ("Raleigh").
3) when you opened up an application, (any application, firefox, gedit, or whatever) it appeared without a title bar, you know, the thing that has the 3 buttons that minimize, maximize, and exit
4) Nautilus was messed up.  I could open up the 'Documents' folder, and the 'File System' folder and some others.  But if I tried to open "Computer" (from the Places menu), then it would come up with the following error message:
                                       
                                    Could not display "computer:"
                                    Nautilus cannot handle 'computer' locations.

A similar message shows when I try to open the Trash, and also the Network.
5) Who knows? I feel like I'm just hitting the tip of the iceberg.  There could be problems without end of which I don't know.

So I solved problem number 3) by adding 'metacity' to the startup applications.  But 1), 2), 4) and 5) remain.

Please help me!  I'm known as something of a "Resident Linux Genius".  Everyone turns to me with their Linux help, and I'm almost always able to help them.  But this drives me nuts!  Our Ubuntu Computer is used on a daily basis, probably an hour a day, 7 days a week.  Its our fastest computer, and if it stops working, then we're in trouble.
](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by blazemore on 2010-01-28
Firstly, try this one:
```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get install --reinstall ubuntu-desktop
```That fixes the majority of package issues for me.
EDIT: Thanks :-)

---

### Post by llawwehttam on 2010-01-28
> **blazemore said:**
> Firstly, try this one:
```
sudo apt-get update; sudo apt-get install --reinstall ubuntu-desktop
```That fixes the majority of package issues for me.

You may want to change that line to ```
sudo apt-get update ; sudo apt-get upgrade ; sudo apt-get install --reinstall ubuntu-desktop
``` so it installs updates before reinstalling the desktop environment.

---

### Post by Rob_H on 2010-01-28
GTK is the underlying toolkit for the GNOME desktop and many apps. My guess is you replaced some or all of the Ubuntu GTK packages with the ones you built. I don't know how you can recover from this other than to reinstall Ubuntu. After that, you can install the GTK development library via the package manager with:

```
sudo apt-get install libgtk2.0-dev
```

---

