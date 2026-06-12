---
title: "Just Desktop Background"
date: 2010-08-13
forum: General Help
---

### Post by qaissi on 2010-08-13
No panels available.

No right click menu.

Can not easily get to terminal.  No function key combinations work.

Did manage to get to a terminal by getting a search window from a keyboard specialty key.  

Once there I tried sudo gnome-panel and got this error:

(gnome-panel:2139): Gtk-CRITICAL **: gtk_accelerator_parse: assertion `accelerator != NULL' failed

** (gnome-panel:2139): WARNING **: Unable to parse mouse modifier '(null)'

** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2139): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

Any Ideas?

---

### Post by earthpigg on 2010-08-13
hi,

at the login screen, can you verify that GNOME is selected at the bottom and not openbox or something else?

can you give us some background on the system? where you trying anything unusual prior to this happening?

---

### Post by qaissi on 2010-08-13
Yes I was booting up normally with the normal Gnome - tried failsafe gnome and got no where.

Just turned the computer on for a new day kind of thing and no desktop.

Did an ubuntu update late last night and was playing Wesnoth but nothing out of the usual.

Brand new system:

AMD Phenom II Quad Black Edition
Asus M4A89GTD Pro motherboard
8 gig of Ram
using the onboard video card Ati

Multi Boot using Grub 2
Ubuntu 10.4
Windows 7
Windows XP

Thank you for any help.

---

### Post by linux18 on 2010-08-13
sudo apt-get clean
sudo apt-get update
sudo apt-get --fix-broken upgrade
sudo apt-get purge gnome-panel
sudo apt-get gnome-panel
gnome-panel

---

### Post by qaissi on 2010-08-13
linux18:  ran your code and got my panels back but without any title bars and the terminal title bar is hidden by the top panel so I can not close the terminal program that way.

Right clicking in the terminal program will let me close the it but when I do I am back to where I started - no panels - no right click menus - the only short cut key combination that works is the ctrl-alt-del to shut down.

I have a find button on my keyboard and when I use that I get the find window open and can get to nautalis that way which allows me to open files in terminal so that is the only way I can get the terminal open.

Right now the only option I have is to rebuild and I really do not want to do that right now since backing up will be difficult given the restraints I currently have.

---

### Post by earthpigg on 2010-08-13
> got my panels back but without any title bars and the terminal title bar is hidden by the top panel so I can not close the terminal program that way.

one final thing i would try before giving up and reinstalling is deleting .gconf from your home folder and restarting.

does the odd behavior you are experiencing happen with other usernames on that computer, by the way, or just when you are loggin in under your normal username?

---

### Post by linux18 on 2010-08-13
for the panel thing type "gnome-panel & disown gnome-panel" then you can close the terminal without disrupting the panel, then goto startup and make sure gnome-panel is a startup item

---

### Post by qaissi on 2010-08-14
Nope nothing helped but thanks anyways - ended up doing a rebuild.

---

