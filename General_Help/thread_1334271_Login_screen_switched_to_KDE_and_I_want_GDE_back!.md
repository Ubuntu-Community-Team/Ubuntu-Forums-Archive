---
title: "Login screen switched to KDE and I want GDE back!"
date: 2009-11-22
forum: General Help
---

### Post by HamletDRC on 2009-11-22
Ubuntu 9.04 

I've been happily using 9.04 with GNome with very few modifications. 

I installed Edubuntu Desktop and it switched my Login Screen to the KDE login screen. I don't like this, so I uninstalled Edubuntu. But my login screen didn't revert back to to the Gnome login screen. 

How can I remove the KDE login screen and revert to the GNome one? 

When I try to launch System->Admin->Login Window, I get the error "GDM is not running"

---

### Post by audiomick on 2009-11-22
Make sure Gnome is still installed, I usually open the package manager and search. 
Having made sure it is still there:
At log-in the is an option somewhere on the screen to choose which of the installed desktops you want to log into. You don't have to do a complete re-start, just log off and back on.
On 9.10 the drop-down doesn't appear until you click on your user name.
On 9.04, I think it is in a "task bar" at the bottom of the screen. There should be an option somewhere to say always boot into this / the last used desktop

---

### Post by HamletDRC on 2009-11-22
@audiomick

I can launch Gnome just fine... it is the login screen itself which is the KDE login screen, not the GDE login screen. The login screen used to have this nice gnome screen and now the login screen is an (IMO) ugly, complicated KDE screen. 

How can I get back to the default login screen?

---

### Post by egalvan on 2009-11-22
You are using Jaunty, so GRUB Legacy is installed.

So use StartUpManager to change KDM to GDM.

It's found under System>Administration

StartUp-Manager

if not installed, install it via Synaptic.

it's the GUI way to change GRUB boot-time parameters.

---

### Post by HamletDRC on 2009-11-22
@egalvan

The Startup-Manager lets me edit the splash screen but I don't see options to edit the login screen. 

By login screen I mean the screen that lets you type in your username and password. It is a KDE based login screen right now and I can't switch it back to the Gnome default login screen. There are no options in the login screen to control how the screen looks.

---

### Post by HamletDRC on 2009-11-22
Aha, I figured it out. KDM has been set to my default desktop manager, so I needed to do this at the terminal: 

    sudo dpkg-reconfigure gdm

And select gdm as default. Then rebooting worked it all out.

---

### Post by egalvan on 2009-11-22
OK, you are right, StartUpManager is not the correct one. Sorry.


Try Boot-Up Manager (also under System>Administration)
and un-check
"KDE Display Manager"
KDM


make sure 
"GNOME Display Manager"
GDM

is still checked


if this does not work, I am out of options/ideas.

---

### Post by egalvan on 2009-11-22
> **HamletDRC said:**
> Aha, I figured it out. KDM has been set to my default desktop manager, so I needed to do this at the terminal: 

    sudo dpkg-reconfigure gdm

And select gdm as default. Then rebooting worked it all out.

Great. Good work.

Can you mark this thread as "SOLVED" so it can help others?

---

