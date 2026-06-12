---
title: "Openbox questions"
date: 2006-04-11
forum: General Help
---

### Post by graabein on 2006-04-11
Hi, I have decided to install openbox and pypanel on my old machine because I find GNOME too slow. Openbox shows up in GDM but where do I find the startup script to load the background image and start pypanel, gnome-volume-manager and gaim?

I also have to adjust the screen fonts. Is that controlled by the current theme (I have ObConf)? Because the Firefox font size in GNOME is all right but it's much too small in Openbox. 

:-k


EDIT: I found running gnome-settings-daemon corrected my second question.

EDIT 2: I also found [this thread]("http://www.ubuntuforums.org/showthread.php?t=23998") but it does not solve my case because I want other users to launch GNOME as default and my own GNOME session should not start pypanel and feh etc.

---

### Post by majikstreet on 2006-04-11
I've never done any of this, but I think you can use xsession files.. 
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)
^^ good xsession howto

in GDM, choose the "Default" session... make .xsession files for every user
for the gnome ones, you would have exec gnome-session at the end of the file..

hth,
majikstreet

---

### Post by graabein on 2006-04-12
Yes I eventually went for that approach. 

When my mom logs in she gets her usual GNOME session and when I log in I get openbox with pypanel and such. When I want GNOME I select it from the session list before I log in and it starts as usual with no pypanel.

Everything seems to be in order, sir.  :D

---

