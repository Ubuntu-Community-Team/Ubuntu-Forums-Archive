---
title: "I want to know how to change x background"
date: 2006-03-01
forum: General Help
---

### Post by defaced on 2006-03-01
I want to know how to change the ugly grey X background.

I cant find it anywhere.

---

### Post by earobinson on 2006-03-01
cant you right click on the desktop to do this?

---

### Post by defaced on 2006-03-01
Not the normal desktop...
THe one that has the x cursor and clock ... with the gray background. before the login screen comes up.

---

### Post by sylvester_0 on 2006-03-01
Get a faster computer. ;) 

But seriously, I doubt this is possible without some kind of changing of the source/recompiling.

---

### Post by defaced on 2006-03-02
well i have a 64 bit machine it is really fast just i don't want to see the ugly grey flash when its loading.

on some version you can add a -br to the line 
defaultserverargs= of startx 
and it will change it to black not sure which file it would be in kubuntu.

---

### Post by incubus on 2006-03-02
defaced,

You got a very good point there. In Ubuntu this is passed to the X server through kdm/gdm. In KDE's case, you have to edit:
/etc/kde3/kdm/kdmrc

and tweak the line:
ServerArgsLocal=-nolisten tcp

I added "-br" there and it works as expected (black screen instead of that old-fashioned looking one).

incubus

---

### Post by R3linquish3r on 2006-03-03
I have the line "#ServerArgsRemote=" is that the same thing?

---

### Post by incubus on 2006-03-04
No, I'm sorry, I was trying to get it from my memory.

You'll change a line containing "ServerArgsLocal" and it should then look something like this:
ServerArgsLocal=-br -nolisten tcp

incubus

---

### Post by super on 2006-03-04
hey! this i flippin brilliant!
what file is it for gnome?

---

### Post by incubus on 2006-03-04
Yeah, this is a nice tweak.

I'm not sure about gdm, but according to this website:
[http://process-of-elimination.net/wiki/Control_Font_DPI_in_X]("http://process-of-elimination.net/wiki/Control_Font_DPI_in_X")

...the file is:
/etc/X11/gdm/gdm.conf

and you append "-br" to the line:
command=/usr/X11R6/bin/X

hope that works,
incubus

---

### Post by defaced on 2006-03-08
Thanks for your help that has been the one thing that bugged me. Thanks again

---

### Post by andreasmascher on 2007-08-16
mmm, I use gnome x server and in the /etc/x11/gdm there is the following line: 


# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 

um, the -br command was there allready. But on start up I have the ugly background thing still. Any advice?

(feisty!)

---

