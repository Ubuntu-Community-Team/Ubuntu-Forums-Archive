---
title: "pidgin issue"
date: 2009-08-22
forum: General Help
---

### Post by djrunslinux on 2009-08-22
Couple weeks ago all of A sudden pidgin started to crash as soon as it connected.The only way I can keep it up is by loading it thru the terminal using sudo.But thats kind of a pain.anyone know why this has happened or are there better alternatives to pidgin?

---

### Post by BackwardsDown on 2009-08-22
Do you get any errors when you don't start it as sudo in the terminal?

---

### Post by djrunslinux on 2009-08-22
no none at all

---

### Post by Nicholasfaz on 2009-08-26
I am having the same problem. The error message i'm getting from the terminal is ----Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Segmentation fault

Any Ideas?

---

### Post by sports fan Matt on 2009-08-26
Well, there is empathy.  It can be installed by pasting this in the terminal: sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn

And you can update sources list by: deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) hardy main 

Note this is for a hardy install but replacing jaunty would work too.

---

### Post by jonobr on 2009-08-26
Do you have any problematic plugins?
I know the skype plugin in for me cuased this problem.

When I do run into this problem from time to time, and I do run into it..

I just mv the .purple directory to a backup,.

And restart pidgin.
It starts the wizard again,and Im starting from scratch.
I can add my accounts using the accounts.xml thats in the back.

Im not sure if thats the way you would like to go, its just easiest for me

---

