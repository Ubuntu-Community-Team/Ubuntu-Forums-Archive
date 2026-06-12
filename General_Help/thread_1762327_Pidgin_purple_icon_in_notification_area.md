---
title: "Pidgin purple icon in notification area"
date: 2011-05-19
forum: General Help
---

### Post by zajc on 2011-05-19
Does anybody know how to get back Pidgin original icon(s) in Xubuntu 11.04 Notification area? I need it because I don't like that blue envelope in Indicator plugin, I would like to use it as "old fashion way".

Here is an example how icon looks like when Show system tray icon is selected.
[IMG]http://www.shrani.si/f/32/kc/1o2UIxPd/pidgin.png[/IMG]

---

### Post by mcclunyboy on 2011-05-19
try looking in 
**/usr/share/pixmaps/pidgin/tray**


I use different OS but if I remember correctly the ICON's were in there

---

### Post by zajc on 2011-05-19
In /usr/share/pixmaps/pidgin/tray I have 2 folders

-hicolor*
16x16  22x22  32x32  48x48  index.theme

*all subfolders are filled with icons (.png files)

-16
available_4bit.ico  connecting_4bit.ico     message_4bit.ico
away_4bit.ico	    extended-away_4bit.ico  offline_4bit.ico
busy_4bit.ico	    invisible_4bit.ico

**Any idea what I've been missing?**

---

### Post by Toz on 2011-05-19
Open Pidgin and goto Tools->Preferences. On the Interface tab, change "Show system tray icon" to Always.

---

### Post by zajc on 2011-05-19
> **Toz said:**
> Open Pidgin and goto Tools->Preferences. On the Interface tab, change "Show system tray icon" to Always.
I did that. The result is purple icon [IMG]http://www.shrani.si/f/32/kc/1o2UIxPd/pidgin.png[/IMG].

---

### Post by Toz on 2011-05-19
> **zajc said:**
> I did that. The result is purple icon [IMG]http://www.shrani.si/f/32/kc/1o2UIxPd/pidgin.png[/IMG].

I'm sorry, I must have misunderstood. What are you trying to do?

---

### Post by axel668 on 2011-05-19
having the same "issue" here ... think he just wants the standard (as in not purple) icons back - maybe could try another icon theme (appearance settings) ?

---

### Post by koper1805 on 2011-05-26
Hi,

go to XFCE-Preferences.
Then go to appearance (Hope it is the English name, I use German here)
There you can change the XFCE Icon themes.. 
All Icon themes called "elementary * "  use this silly purple bubble thing..
So change to another Icon theme and everythings all right.

Cu.
Christoph

---

### Post by axel668 on 2011-05-27
> **koper1805 said:**
> Hi,

All Icon themes called "elementary * "  use this silly purple bubble thing..
So change to another Icon theme and everythings all right.



Some use a silly purple penguin, too ;)  But Christoph's right, just try some of the icon themes and sooner or later you'll run into one showing correct status icons

---

### Post by zajc on 2011-05-30
Thanks, this has solved my problem :P

---

### Post by Dawa on 2011-08-05
Sorry to drag this up again, but...

What if you don't want to change your icon theme?  Any way to manually add the correct pidgin tray icons?

Also I'd like to just add that icon themes adding their own app-icons is annoying/stupid.

---

