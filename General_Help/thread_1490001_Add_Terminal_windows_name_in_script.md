---
title: "Add Terminal windows name in script"
date: 2010-05-21
forum: General Help
---

### Post by jee_bee on 2010-05-21
very simple but i cannot find the working command anywhere
i want to give terminal windows name when i start an app from a script
when i type in echo --help just send my back --help =D> lol


 
> #!/bin/bash
echo  **????????? thats what i need** (ESC]2;"THENAMEIWANT"^G IS NOT WORKING)
cd /srv/ventsrv
./ventrilo_srv



thx..

---

### Post by bodhi.zazen on 2010-05-21
I can not divine what name you want.

You want a "title" or name on your terminal ?

gnome-terminal --title foo 

It would help if you described what you are wanting and tell us what terminal application you are using.

---

### Post by jee_bee on 2010-05-21
im using gnome terminal and ur gnome-terminal --title whatiwant is not working it only pop on a second terminal the title on top of the windows change for half a second and came back to the normal


thats the title of de terminal i want to change
so i can be able to identify server in taskbar

---

### Post by gmargo on 2010-05-21
The standard escape sequences to write to the window title and icon attributes are:

```
ESC ] 1 ; <your text goes here> ^G     - change the icon name
ESC ] 2 ; <your text goes here> ^G     - change the window title
ESC ] 0 ; <your text goes here> ^G     - change both
```For instance, the following command will write "Hello" to your window title:
```

/bin/echo -e "\033]2;Hello\007\c"

```

---

### Post by dcstar on 2010-05-21
> **jee_bee said:**
> im using gnome terminal and ur gnome-terminal --title whatiwant is not working it only pop on a second terminal the title on top of the windows change for half a second and came back to the normal


If you edit the Default Terminal profile there is an option to keep the initial title, the default setting replaces the title and you see what you are now getting.

Once you change this you should be able to launch the gnome-terminal with a name derived from the system name:

```
gnome-terminal --title $HOSTNAME
```
You should be able to make an alias of this on whatever systems you connect to. **

** Apparently some older versions of gnome-terminal had a bug in the title setting that was only recently fixed, so on some old system it may not work correctly.

---

### Post by bodhi.zazen on 2010-05-21
Open your terminal

Go to Edit -> Profile preferences

Go to the "Title and command" tab

In the "When terminal commands set their own titles" choose "Keep initial title"

You may then use

gnome-terminal --title thanks.bodhi

=)

While you are there you may wish to look at some of the other options, can't hurt ...

---

