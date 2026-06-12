---
title: "Display box design - Server 9.10 and LXDE"
date: 2009-12-01
forum: General Help
---

### Post by Drone86 on 2009-12-01
Hi,

I'm putting together a remote display box (like an advertising or information screen). 
All it needs to do is boot up and display a web page or projector program, so I'm looking for a quick, lightweight, simple and very reliable setup that can be left on its own pretty much forever except for the occasional remote access via telnet/VNC. It will have no HIDs (mouse, Keyboard).

I'm a linux novice, most complicated thing I've done so far is get a ZTE MF636 modem working according to [http://www.matt-barrett.com/?p=5](http://www.matt-barrett.com/?p=5) (and a few fixes).

What I have so far:

OS: Ubuntu 9.10 Server (prototyping on VirtualBox) 
GUI: LXDE (latest ver as of 15-11-09)

1. Get modem working - [COLOR=Green]check[/COLOR]

2. Get WVDial working with non-root user (to auto dial out): [COLOR=Red]Fail[/COLOR]

Intended operation: Box boots, auto dials out on 3G modem, maintains live connection.
Failboat: pppd dies (Error 2).

"sudo wvdial" works, but requires a user input that isn't possible - password. I've tried all techniques on here - [http://wiki.archlinux.org/index.php/Allow_users_to_dial_with_wvdial](http://wiki.archlinux.org/index.php/Allow_users_to_dial_with_wvdial) - but I still get pppd dying if wvdial not run with sudo. 

Since this is an automated process, though, could I use a script which belongs to root to start wvdial as a service? (Shaky understanding, please fill in). How would I do this?

3. Auto-login LXDE - [COLOR=Red]Fail[/COLOR]

Intended operation: Box boots, starts LXDE window manager, goes straight to blank desktop (no menus, no nothing). Projector app or browser window starts and fills screen. 

Failboat: I have an Ubuntu Desktop Virtualbox, Auto-login is used as an option. However, when installed on Ubuntu Server I get nothing, it has to come up with a login prompt. Could I:

i) Auto-login by some other mechanism, and if so, what mechanism...or
    (ii) Make the browser or projector program appear over the top of the login prompt.

I would like to stick with Server and not Desktop because of its bare minimal construction. If something breaks its going to be expensive and time-consuming to go fix it in person so I'd like to make it simple and as solid as possible.

4. Get LXDE to boot in normal graphics mode without screen.

Intended operation: The screen will be powered down to start with (external control), once its booted and ready to display the screen will power up. 

Failboat: Still at the shipyard - don't know whether its gonna sail. I haven't tried it yet but I've come across threads on here where people have had problems with headless boxes - so I'm anticipating a problem.


So thats where I am at the moment, still searching and experimenting so will update this thread as I find stuff. Suggestions are extremely appreciated. Cheers!

---

