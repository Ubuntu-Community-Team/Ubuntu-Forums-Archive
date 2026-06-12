---
title: "bash ___ permission denied??"
date: 2011-07-26
forum: General Help
---

### Post by steven_191 on 2011-07-26
in terminal ive written this

/etc/pptpd.conf

to see the options in a pptp VPN

this gives me 

BASH: /etc/pptpd.conf: persimission denied.

what does this mean?

if i type nano before i get a write up of information but it says read only so i cant do anything to it.

---

### Post by SlugSlug on 2011-07-26
if your wanting to edit the file try 

gksudo gedit /etc/pptpd.conf

this will open gedit with root (sudo) rights

---

### Post by steven_191 on 2011-07-26
thats opens up the file for editing

thanks

what does the gksudo gedit mean then?

---

### Post by blind2314 on 2011-07-26
Gksudo means "elevate my user ID's permissions temporarily to "superuser", and do so for graphical programs". Gedit opens up the graphical text editor that GNOME uses by default.
 
Together, gksudo gedit means open up a graphical text editor with elevated permissions (So you can work on or edit files that are normally restricted to anyone but root. System config files are a good example).
 
EDIT:
 
Also, if you just want to see the contents of the file, you can use ```
 cat <filename> 
``` or ```
 less <filename> 
```.

---

### Post by bodhi.zazen on 2011-07-26
For additional information on gksu, see

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by steven_191 on 2011-07-26
so what does it mean if i edit the file, save and close it, then the terminal says something about it not working and not being saved. But if i go back into the file it displays what i have changed?

---

