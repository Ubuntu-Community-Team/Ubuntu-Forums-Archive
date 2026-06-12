---
title: "Removing XGL/Compiz"
date: 2006-06-25
forum: General Help
---

### Post by mikaPELL on 2006-06-25
I am seriously ripping my f%¤#&ng hair out here! I installed XGL/Compiz just to test it by following this tutorial: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) . It was cool for like five minutes, but my sh¤&#y hardware took away all the fun because of the bad performance, and when I closed a seemingly useless terminal window, everything hung up, all of the window borders disappeared and I was unable to change applications or anything at all. At the next reboot I decided to remove the crap, and after apt-get removing xserver-xgl, compiz and compiz-gnome, it actually *boots* into borderless-useless mode. 
My throat is suffering from me being ill, and if it wouldn't end up with me coughing blood all over the place, I would literally scream my lungs out in pure frustration right now. ](*,) 
The "PC" I'm using has an AMD processor, and a Radeon 9200 graphics card.
I would really, *really*, ***really,*** ***_REALLY_*** appreciate any forms of help.

---

### Post by joshrobinson on 2006-06-25
```
sudo gedit /etc/gdm/gdm.conf-custom
```

remove this section so that just [servers] tag remains

```
 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```

change it so it looks like this

```
 [servers] 
```

next

```
sudo gedit /etc/gdm/gdm.conf
```

change this ```
#0=Standard
1=Standard
```

to this

```
0=Standard
#1=Standard
```

and this
```
GdmXserverTimeout=50
```
to this
```
GdmXserverTimeout=10
```

and finally remove the start compiz script from your sessions

then u can uninstall the packages in synaptic
reboot and should be ok

P.S. if you cant get into the X gui or the Xgl gui, replace the gedit command with nano

---

### Post by mikaPELL on 2006-06-25
Thanks a million! I did this (as root in maintenance mode), but it's exactly the same now. Do you have an idea on how I can remove the script from my startup session from the terminal?

---

### Post by joshrobinson on 2006-06-25
[QUOTE=mikaPELL]Thanks a million! I did this (as root in maintenance mode), but it's exactly the same now. Do you have an idea on how I can remove the script from my startup session from the terminal?[/QUOTE]

you can startup into x without deleteing it, beccause it will just try to boot compiz and fail.. it shouldnt mess anything up doing that.. you can just wait till you get into x and remove it from sessions, or you can remove the file that is in sessions

sudo rm /usr/bin/startcompiz

---

### Post by mikaPELL on 2006-06-25
Hmm, then that can't be the problem, because even after removing startcompiz, I have no window borders, and can't do anything after logging in. I have no gnome-panel, and I can't change windows with Alt-Tab. I don't know what to do at all! I can't do a clean install before I have backed up, and I want to get this fixed before I do that. Please help me!

---

### Post by w1z4rd on 2006-06-25
I feel your pain man, Im busy going through this. Im a KDE user, and Im trying to remove xgl so I can game on cedega for a bit.

Here what I did (Im a n00b):

```
sudo aptitude purge compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
``` 

Bye bye desktop, tends to take most of the desktop with it (in my case it was kde). I then rebuilt my xorg.conf file from that command thats in it.

I then rebuilt X, and then KDE from scratch. When I got to that server problem, it was in my case: /etc/kde3/kdm/kdmrc

My friend who has helped me setup X, and just killed the server command that I had wanted to restore, and so from a lot of googling, i came up with this change:

```
ServerCmd=/usr/X11R6/bin/X -br -novtswitch -sharevts  vt7
#ServerCmd=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

```

I think were basicaly telling the desktop to connect to whatever X server, and since weve downed the xgl part of things we cant connect to it. Well thats my guess anyways.

#ing out that XGL line, and putting that other line in has enbled me to boot up into kde with what looks like a perfect recover. Except for one thing. When it loads the login screen, my usb keyboard stops working, my mouse is fine, and when i use it to start a console terminal, it works, and i can type in console when i am out of X and KDE.

Right now Im loaded into gnome so I dont thing theres anything wrong with that server command. I think prehaps there might be something with my xorg.conf

If anyone can help me out with that heres the code:

[http://www.pickledbushman.com/xorg.txt](http://www.pickledbushman.com/xorg.txt) (the #'d out freetype is irrelevant, it wasnt working before i put that there, im just trying everything I can think of.

There was one other thing... I remember having to do something funny to a file some where... in ended in main, and I had to put a # at the end of main (long day, many attempys)... so yeah. help:)


Edit: have since discovered the mystery #:

There were my instructions to put them in:
> After making that change, proceede to edit /usr/bin/displayconfig-restore (as root) and place a comment in the last line, making

Code:

#main()


the last line.

let you know now what happens when i uncomment it.

---

### Post by joshrobinson on 2006-06-25
when you get into normal X/gnome type this command in a terminal

```
metacity --replace
```

that should give you your window borders back 

then go into system, preferences, settings and remove the compiz script if its in there

next time you restart if the window borders dont come back again you can create a script to put in sessions that will start up metacity for you on boot.. but if you really want to reinstall you wont have to bother doing that, just backup your stuff and reinstall

if you want to make a metacity startup script, create a new document in your home folder, call it metacity, and put the following in it and save it.. 

```

#!/bin/bash
metacity --replace

```

then in a terminal change directory into your home folder and do 

```
sudo chmod +x metacity
```

then add it to your sessions/startup scripts like you originally did for the startcompiz script

EDIT: i just saw that you have no gnome panel.. so opening a terminal would be a pain if you dont have a keyboard shortcut or a desktop link for it

how much data do you have to backup? and what would you be backing it up to? you might be able to do everything command line (ive had to before) maybe we can help you with that.. if you had an external usb hard-drive that would be the easiest

---

### Post by RAOF on 2006-06-25
[QUOTE=w1z4rd]...
```
sudo aptitude purge compiz xserver-xgl libgl1-mesa **xserver-xorg** libglitz-glx1 compiz-gnome
``` 
...[/QUOTE]
Just in case you didn't know, the bolded bit is the reason you lost your desktop.  Xserver-xorg is the default X server - without it, you have no GUI **at all**.  All of the desktop packages depend upon it, so by removing it...

Additionally, you wouldn't want to remove libgl1-mesa (or possibly libglitz-glx1).  They're there in a standard install, and things will probably break without them.

Really, all you want to remove is xserver-xgl and compiz.  Everything else can (probably) be left as it is.

---

### Post by Bokonon on 2006-06-26
Compiz/Xgl is indeed touchy.  I never crashed my system so hard as when I was playing with it early on.  ](*,) 

I am sure that there are ways to fix it and get it back, but with all the howto's, hints, suggestions and tricks out there, it is amost impossible to remove everything or reset things back to the way they should be unless you write down everything you do.

Making backups of all files before you start is a big help and may save you, but it is probably too late if you haven't done that.

My solution was a reformat, which was no big deal since I was just testing dapper out on that system.  It only took me a few hours and I was able to watch movies, so it wasn't a total waste.  After that, I took my compiz install very seriously and have it working fairly well now, but I have the separate Xgl session install, so I can always go back to X if things get hairy.

---

### Post by joshrobinson on 2006-06-26
[QUOTE=RAOF]Just in case you didn't know, the bolded bit is the reason you lost your desktop.  Xserver-xorg is the default X server - without it, you have no GUI **at all**.  All of the desktop packages depend upon it, so by removing it...

Additionally, you wouldn't want to remove libgl1-mesa (or possibly libglitz-glx1).  They're there in a standard install, and things will probably break without them.

Really, all you want to remove is xserver-xgl and compiz.  Everything else can (probably) be left as it is.[/QUOTE]
nice call, i didnt even notice that.. doing a sudo apt-get install ubuntu-desktop might help

---

### Post by rickyrockrat on 2007-12-04
The key to getting your window borders back (Kubuntu) is, from an xterm, doing:
kwin --replace 
I *think* gnome's (Ubuntu) is
metacity --replace

---

