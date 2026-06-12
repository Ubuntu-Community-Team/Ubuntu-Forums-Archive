---
title: "&quot;command line&quot; panel applet - shortcut?"
date: 2006-03-21
forum: General Help
---

### Post by nanotube on 2006-03-21
Hey all,

I have added the "command line" applet to my panel, because it seemed like it would be very convenient - but after looking around i have not been able to find a way to set a keyboard shortcut to send focus to the applet, so currently the only way is to use the mouse and click in it, which is far from convenient.

does anyone know if it is possible to set up a shortcut to send focus to the applet, and if so, how? 

thanks!

---

### Post by blackbeastofaarrgh on 2006-03-21
Alt+F2 brings up a command box. Same thing, basically.

---

### Post by nanotube on 2006-03-21
thanks blackbeast, but i already know about alt-f2.
problem is, alt-f2 'run application' box does not have custom macro capability (like automatically opening urls with browser, and other nifty things like that). that's why i was trying to essentially have and alt-f2-like shortcut to bring me to the applet. :)

---

### Post by akiro.yamamoto on 2006-03-21
You can use the:
System >> Preferences >> Keyboard Shortcuts
To create a shortcut to Open the terminal... 8)
Hope this helps ;)

---

### Post by nanotube on 2006-03-21
thanks akiro,
but i already have a shortcut for the terminal, and it works well when i need it. :)
but i was hoping to have a shortcut for the commandline applet, specifically, because that avoids opening up a whole another window, plus has those neat macros.
nice try, though. ;)

---

### Post by akiro.yamamoto on 2006-03-21
My bad, I thought you just needed a fast way to get to the command  line :oops:

---

### Post by nanotube on 2006-03-21
no prob my friend. :) i did indeed need a fast way to get to the cli, but just to that particular one. ;)

---

### Post by akiro.yamamoto on 2006-03-21
Is it easier to create macros and use them in that panel command-line ,than to use scripts in the terminal??

---

### Post by klahjn on 2006-03-21
if you go into your gconf-editor you can link a command to a keyboard shortcut.  If you make a script and put it in /usr/bin or /usr/local/bin or one of those areas, then you could essentially pull up that script or whatever from that one keystroke, just a thought....

---

### Post by nanotube on 2006-03-21
akiro: it's not easier by much, but it's right there on the panel, and it seems so deceptively convenient that i want to try and get it to work right. :)

klahjn: i've thought of using a custom shortcut for this - but do you know of a way to move focus around in x through commandline? i was thinking maybe something with xproc, but couldnt figure out if it could do that...

---

### Post by engla on 2006-03-21
deskbar-applet is a replacement for the mini-commander (among other things). It has the capability to use a key shortcut (in gconf for the breezy rep version, otherwise you can install 0.8.8 from source)

---

