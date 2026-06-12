---
title: "Galeon Stopped working and other things..."
date: 2006-03-18
forum: General Help
---

### Post by jhbumby on 2006-03-18
I was using Galeon just fine for most of my internet stuff when suddenly, I click on it, it shows it in the panel, the mouse does that spin hold on a minute thing, and then it just quits out before a screen even pops up.  What is the deal????  

Also, I download stuff from Synaptic.  Everything goes great, but I can not find the program in the applications button at all.  Where the heck does this stuff go.  It happens to me all the time.  Is there a place this all goes, and can I add them to the applications button if and when i find them???  

Feels great to be back- Thanks,
JohnnyB

---

### Post by jerrykenny on 2006-03-18
Hi JohnnyB welcome back,  try launching the offending programme from a terminal,  then you'll get some feedback from your machine which you can cut n paste here for more help . . . 

Alas, just installin a programme using synaptic doesn't always add a menu item . . . . in which case you have to do it yourself . . . . 

Look at the ubuntu start guide, then go to the page for installing the "dvdrip" programme. . . . it has a nice example of how you can write your own desktop-menu-additions.

Alternately, just add a "custom launcher" to your toolbar . . . . probably easier for a single user machine.

---

### Post by jhbumby on 2006-03-19
How do i add a custom launcher to my desktop?  Also, once I download any of these programs from Synaptic, and they don't show up as a menu item, where do they go???  This has been bugging me since starting up with linux, I can never find the applications that I download.  Thanks again - 
JohnnyB

---

### Post by turtlefreak on 2006-03-19
just use firefox instead. not all applications make entries to the shortcut bar

---

### Post by jhbumby on 2006-03-19
Yeah, I got that part turtlefreak, what my questions was is how do i get to the ones that don't make the "shortcut bar".  Obviously I don't want to use firefox if I was asking about galeon.  We all have our preferences.  Firefox is great for some things, but I find galeon good for others.  I'll restate my two problems Now:

-How do i get to the applications that I download --- the ones that don't show up on the so called "shortcut bar"

-How do I run a program in terminal

Thanx

---

### Post by zoiks on 2006-03-19
[QUOTE=jhbumby]-How do i get to the applications that I download --- the ones that don't show up on the so called "shortcut bar"

-How do I run a program in terminal

Thanx[/QUOTE]

To set up shortcuts: click on "Applications | System Tools | Applications Menu Editor" to add a new menu entry.  (Click "New Entry", and proceed.  You can also right-click on existing entries to change their properties.)  Once the menu item's been added, you can then right-click on that selection in the menus, and choose "Add this launcher to panel", and it will appear on your panel.

To run the program in a terminal, type its name.

---

### Post by jhbumby on 2006-03-19
For Galeon, I get this:
XXXXXXX:~$ galeon
plugin_get_value 1
plugin_get_value 2
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

> "To set up shortcuts: click on "Applications | System Tools | Applications Menu Editor" to add a new menu entry. (Click "New Entry", and proceed. You can also right-click on existing entries to change their properties.) Once the menu item's been added, you can then right-click on that selection in the menus, and choose "Add this launcher to panel", and it will appear on your panel."

As for this, I understand.  But in order to add anything, I need to know where it goes.  Think extremely basic.  When I download something from synaptic, where does it go???  What file is it put into, or whatever???  To add a new menu entry, I have to find the thing I want to add, where is it???
THX

---

### Post by jerrykenny on 2006-03-19
Jhumby,

when you download a programme (say kword for instance) it usually puts the executable in  the subfolder /usr/share/bin

So the correct command would be  /usr/share/bin/kword

But most linux distros will launch kword if you just type    kword   (it knows to have a good rummage in ?usr/share/bin    anyway)

Try it, go to Applications, Accessories, Terminal,  and when the terminal is open just type    firefox, or nautilus    and hit enter.

To create a custom application launcher,  do a right click on the toolbar somewhere and select

Add to panel
Custom Application Launcher

you just have to type in the correct command  eg  kword, or firefox,  Type in an informal sort of Description, and pick a nice icon. . . .

---

