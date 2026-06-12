---
title: "No Menus on Ubuntu 10.10 Gnome"
date: 2010-11-19
forum: General Help
---

### Post by Big Ed on 2010-11-19
I updated my Ubuntu 10.10 yesterday with Synaptic but didn't reboot until this morning.  I can log in normally but that's it.  I get a nearly blank screen with my selected wallpaper.  There is no menu bar at the top of the screen (Menus for Application, System, etc; clock, cpu load, weather, network applets) and no taskbar at the bottom of the screen.  I was able to get Firefox going by opening the one icon I had for an automatically mounted filesystem and going to "Get Help Online" in the Help menu.  I can do little else.  If I right-click on the screen, I get the menu to make folder, make document (which works), but the change background item doesn't run.

I can't switch to a terminal with Ctl-Alt-F7 and I can't see any way to open a terminal in Gnome without the Application menu.

Anyone able to give me some pointers on this?

Thanks,
Ed

---

### Post by Hippytaff on 2010-11-19
You should be able to open a terminal with CTRL+ALT+T
 
if you get one open try
```

sudo apt-get update && sudo apt-get upgrade

```
and 
```

sudo apt-get dist-upgrade

```

---

### Post by Big Ed on 2010-11-19
Thanks for responding.

I got the terminal open.  (Didn't know that trick.  Thanks.)  Ran the commands and got:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

for both upgrade and dist-upgrade.  Tried rebooting anyway (with Ctl-Alt-Del) and it came up the same as before: no menus, taskbars, etc.

I've got all the USB devices (printer, webcam) unplugged and I don't know what to try next.  

Ed

---

### Post by Hippytaff on 2010-11-19
Ok
 
You might not want to do this because it involves removing the desktop and reinstalling it, but that is probably what I would do, but you might have to reinstall any extra pakages you had (ie not installed as default as part of the ubuntu desktop) (not sure) :-)
 
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```

---

### Post by Big Ed on 2010-11-19
That fixed it.  When the ubuntu-desktop was reloading, I noticed that Evolution was included.  I use Thunderbird so I'd removed a bunch of Evolution stuff right after upgrading from 10.04 to 10.10.  I always do this and haven't had a problem before, but I must have deleted one more piece than I usually do and pooched the system.

Thanks for the help.  I'll be a little more careful about what parts of Evolution I get rid of this time.

Ed

---

### Post by Hippytaff on 2010-11-19
Glad it's sorted :-)

---

### Post by malachi-25 on 2011-01-20
I tried everything that you guys wrote in this thread and I still don't have the top bar or the left hand menu.  i have an Acer Aspire 5100 Laptop.  and Ubuntu is a fresh install.
getting frustrated.   I like the new menus and the workspace switcher.
but I can't see them

I even tried to go into the gconf-editor and set the menus_have_icons   and nothing happened.
I do have the netbook edition of ubuntu

Malachi

---

### Post by Hippytaff on 2011-01-21
Hi
 
What graphics card do you have? Also did you say you tried reinstalling ubuntu-desktop? I think Acer Aspires have some quirks with Ubuntu might be worth having a scout on the forums :?
 
Edit -> Had a thought, and yes it did hurt, Might be a resolution thing and the reason the panels are not appearing is bacuse they are 'off' the screen - if you know what I mean

---

### Post by malachi-25 on 2011-01-21
I don't have it here with me at school.  but I think that the Graphics card is an AMD 64.   and they are on the screen.   just blank spots where they should be.  I can still click on them I just can't see them.   
when I hover over the left menu and use the scroll on my mouse they half way appear but then disappear.  I did try the remove and install   both ubuntu-desktop and ubuntu-netbook.  being that it is the netbook edition.


Malachi

---

### Post by Hippytaff on 2011-01-21
When you get back from school, boot into ubuntu, press CTRL+ALT+T to open a terminal and post the output of
```

lspci | grep graph

```
that will give you the graphics card details...you can open firefox (which ships with ubuntu) by typing firefox in the terminal.

By the way, it migh tbe worth starting a new thread with the details you discover ;-)

---

### Post by malachi-25 on 2011-01-21
will do.   I won't be on untill late tonight.   but I will post the thread inside this thread. 


Malachi

---

### Post by Hippytaff on 2011-01-21
cool - don't be afraid to start a new thread, it's less confusing and as this one is marked as solved other people probably won't chime in to help :-D

---

### Post by malachi-25 on 2011-01-21
[http://ubuntuforums.org/showthread.php?p=10383917](http://ubuntuforums.org/showthread.php?p=10383917)

Here it is.  took me a little bit to figure out where to start a new thread  lol.  but I found it.


thanks 
Malachi

---

### Post by Hippytaff on 2011-01-21
> **malachi-25 said:**
> [http://ubuntuforums.org/showthread.php?p=10383917](http://ubuntuforums.org/showthread.php?p=10383917)

Here it is.  took me a little bit to figure out where to start a new thread  lol.  but I found it.


thanks 
Malachi

The forum is yours as much as anybody else's :-)

---

### Post by sshark on 2011-01-24
> **Hippytaff said:**
> Ok
 
You might not want to do this because it involves removing the desktop and reinstalling it, but that is probably what I would do, but you might have to reinstall any extra pakages you had (ie not installed as default as part of the ubuntu desktop) (not sure) :-)
 
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```

This really helpful. It saves me from reinstalling the whole sys again. thanks :)

---

### Post by Hippytaff on 2011-01-24
Hi sshark - Welcome to the forums, glad it helped :-)

---

### Post by icouldmakeyousmile on 2011-03-31
> **Hippytaff said:**
> Ok
 
You might not want to do this because it involves removing the desktop and reinstalling it, but that is probably what I would do, but you might have to reinstall any extra pakages you had (ie not installed as default as part of the ubuntu desktop) (not sure) :-)
 
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```

Yet another thank you. I was reading this on my phone, wondering if I'd have to do another install. Posting on my restored system :)

I too "pooched" my system thinking I could clean up and get rid of Evolution. It's nice to see every mistake I make has been done before.

---

### Post by Hippytaff on 2011-03-31
> **icouldmakeyousmile said:**
> Yet another thank you. I was reading this on my phone, wondering if I'd have to do another install. Posting on my restored system :)

I too "pooched" my system thinking I could clean up and get rid of Evolution. It's nice to see every mistake I make has been done before.

You're welcome - glad it helped :-)

Edit -You should be able to remove evolution without any repocussions, unless you accitendally uninstalled some dependancies

Edit - as a test I just removed Evolution and my system is fine...I did this

```
sudo apt-get remove evolution
``` just incase you want to get rid of it

---

