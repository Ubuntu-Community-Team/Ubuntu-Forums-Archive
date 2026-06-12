---
title: "Installed Application By Synaptic &amp; It's Invisible"
date: 2009-09-03
forum: General Help
---

### Post by shy_guest on 2009-09-03
[SOLVED]In Jaunty, I used Synaptic Packet Manager to install a chess database application called **scid** as it wasn't listed with add/remove. It shows as installed in Synaptic, but it isn't visible in the Games menu for applications, or in any of the other menus, & it doesn't show as installed in add/remove.

Where are packages installed to ? How do I start it ? How do I put it in the Games menu ?

---

### Post by x C0MMAND0 x on 2009-09-03
Try opening it through the terminal.  

Go to Applications>Accessories>Terminal

When it loads, type "scid" and hit enter...what happens?

---

### Post by Clarke on 2009-09-03
Hi! First of all you can try to run "dpkg -L scid" to get information about location of all files from the package.
To get the list of executables try dpkg -L scid | grep bin/

---

### Post by shy_guest on 2009-09-03
Ok , it works in the terminal. Does that mean that I am always going to have to run it in the terminal (**surely not - this is Linux!!!**). How do I edit the menu bar ? & why does it not show up in add/remove ?

---

### Post by x C0MMAND0 x on 2009-09-03
Go to System>Preferences>Main Menu 

Choose "Games" from the left, Then click "New Item" on the right.  

Type - Application
Name - (whatever) "Chess" or SCID for example
Command - scid
Comment - (whatever you want)

Now it will be under applications>games for you.

---

### Post by moster on 2009-09-03
Or you could install "gnome do". It is for more stuff, but I use that as app launcher.

For example, press "c" and it finds all installed apps starting with. Very useful.

---

### Post by shy_guest on 2009-09-03
Thanks to everyone for your prompt & helpful replies.

---

