---
title: "trouble with installing the vista menu bar/task bar"
date: 2009-11-08
forum: General Help
---

### Post by lucas_87 on 2009-11-08
hi people i'm new to ubuntu and i guest ubuntu is new to me as i've got 9.10 karmic koala or something anyway...

i'm trying to install the vista menubar ive typed in the command in the terminal:

"sudo apt-get install python2.5 python-xdg python-cairo python-gconf python-xlib deskbar"

and i keep getting this response: "Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.5 is already the newest version.
python-xdg is already the newest version.
python-cairo is already the newest version.
python-cairo set to manually installed.
python-gconf is already the newest version.
python-gconf set to manually installed.
python-xlib is already the newest version.
python-xlib set to manually installed.
E: Couldn't find package deskbar"

can you please help me install this thing!?

i swear theres no need for stupid codes why cant it be as easy as just click install and a few next buttons then finish. windows is much easier to use BUT it is slow compared to ubuntu i guess thats the sacrifice eh?

any help will be much appreciated. ^_^

---

### Post by Uncle Spellbinder on 2009-11-08
Never heard of vista menu bar/task bar for ubuntu. If it's not in the repos (and the term *couldn't find package deskbar* indicates that it's not), I'd search the [PPA's](https://launchpad.net/ubuntu/+ppas) or an official repo and add it to your sources list. 

Curious to see this vista menu bar/task bar. Look forward to this being answered.

---

### Post by munky99999 on 2009-11-08
> python-xlib is already the newest version.
python-xlib set to manually installed.
E: Couldn't find package deskbar"
Everything installed except deskbar. As that package doesnt exist.

"sudo apt-get install python2.5 python-xdg python-cairo python-gconf python-xlib deskbar-applet"

Probably what you want to run.

I think though that you want to get the cairo dock.

sudo apt-get install cairo-dock

I really dont know though. Perhaps you could explain what you're trying to get? Perhaps a link or something?

---

### Post by munky99999 on 2009-11-08
[http://www.gnome-look.org/content/show.php?content=71425&forumpage=22&PHPSESSID=6]("http://www.gnome-look.org/content/show.php?content=71425&forumpage=22&PHPSESSID=6")

I found what he was looking at I think.

All you need to do is download the template from that website. 


(VistaMenu 1.08 beta (Ubuntu/Debian)) one will give you a deb file that will install nice and quickly.

---

### Post by Uncle Spellbinder on 2009-11-08
Last updated a year ago. Compatibility issues with the new Karmic is quite possible.

---

