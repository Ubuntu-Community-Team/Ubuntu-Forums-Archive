---
title: "Safe way out of Safe Mode?"
date: 2010-08-23
forum: General Help
---

### Post by jarviser on 2010-08-23
I tried out Safe Mode in 10.04 and did a Fix Broken Packages for the heck of it. I then selected continue normal boot from the safe mode menu and it asked for login and password but then it left me in full screen terminal mode. I didn't know how to get the Gnome desktop back, which I would consider as a "normal boot, so I hit the power switch.

What should I have really done to get into Gnome?


As a couple of observations I did notice that to repair packages you need to have ethernet connected, not wifi.  
I also noticed that to get the safe mode menu on second attempt, the safe mode menu only flashed up and I had to cursor up and down to "reveal" the menu.

---

### Post by coffeecat on 2010-08-23
> **jarviser said:**
> I tried out Safe Mode in 10.04 and did a Fix Broken Packages for the heck of it. I then selected continue normal boot from the safe mode menu and it asked for login and password but then it left me in full screen terminal mode. I didn't know how to get the Gnome desktop back, which I would consider as a "normal boot, so I hit the power switch.

What should I have really done to get into Gnome?

I presume you mean Recovery Mode.

When you continue normal boot after using one of the recovery mode options you are taken to the login for virtual terminal 1, which normally doesn't run with a GUI. After logging in you could have started the GUI with the command 'startx', but that's a bit messy because you need to enter your keyring password to get the wireless up. You normally don't get prompted for the keyring password when you log in via the GUI.

Probably quicker and easier is once you've done the fix broken packages (or whatever) is to drop to a root prompt (It's down the bottom of that menu somewhere). You are given a '#' root prompt. Now simply use the command 'reboot' and reboot in normal mode into a GUI.

> **jarviser said:**
> As a couple of observations I did notice that to repair packages you need to have ethernet connected, not wifi.

That's because in normal operation wireless connections are controlled by the GUI gnome app network-manager. No GUI = no network-manager running.

---

### Post by jarviser on 2010-08-23
> **coffeecat said:**
> I presume you mean Recovery Mode.


Oops! showing my windoze! Yes. Thanks for the advice, I'll try it out.

---

