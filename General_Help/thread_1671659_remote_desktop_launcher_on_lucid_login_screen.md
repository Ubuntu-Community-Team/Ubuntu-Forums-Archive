---
title: "remote desktop launcher on lucid login screen ?"
date: 2011-01-20
forum: General Help
---

### Post by chrisdee on 2011-01-20
Hello.

I'v been google'ing for months after a solution to put an remote desktop launcher on the lucid login screen.
But I just can't find any examples or suggestions.

I'm running a ubuntu lab, and adding an rdesktop launcer to the login screen would really make login much easier for the users, so they don't have to login twice. First into lucid and then into windows with rdesktop.

I'v already made the rdesktop launcher on the lucid desktop, but where (if possible) do I put it so it will also be avalible in the lucid login screen ?

This is my last effort to try to get this to work.
Any experts here wich know how to do this ?

---

### Post by chrisdee on 2011-02-01
Bump

---

### Post by TheHackOps on 2011-02-01
Sounds like one hell of an edit

---

### Post by Krytarik on 2011-02-01
You may try to put the "*.desktop" file of the launcher into "/usr/share/gdm/autostart/LoginWindow". But you have to consider, that the launcher will be run as the user "gdm" then! If it works that, you could remove "Login Window" (gdm-simple-greeter.desktop) from that directory.

---

