---
title: "Maverick with old netbook interface - how?"
date: 2010-10-10
forum: General Help
---

### Post by Ichtyandr on 2010-10-10
Dear Netbook users,
What is a simple way to get 10.10 with old (Lucid-style) netbook interface, e.g. if you install from alternate or minimal install image
thanks

---

### Post by kerry_s on 2010-10-10
the 2d version is still in the repos.

---

### Post by Ichtyandr on 2010-10-11
thanks for your reply, I want to run Maverick on netbook but want to install a regular old 3d lucid netbook interface on 10.10 from cli (or from desktop install) and wonder if there is a metapackage / command for that

I feel rather comfortable with old netbook style as it still saves vertical space more than regular desktop

---

### Post by kerry_s on 2010-10-11
like i said, netbook-launcher is not even in the repo no more, its gone, but the 2d netbook-launcher-efl is, so that's the only option for that interface. you'll have to run it as a app in what ever wm/de you choose to use, that means adding it to startup.

---

### Post by Mrmental on 2010-10-11
I got a passable imitation of Lucid's interface going in maverick using EFL.

1: I installed netbook-remix-efl, maximus, go-home-applet and window-picker applet
2:When installed, log out and start an ubuntu netbook 2D session
3: Remove the bottom panel, remove the main menu and window list applets from the top panel
4: Add go-home-applet and window-picker-applet to the top panel.
5: Make sure you start add maximus to your startup applications

Login and logout and you're good!

---

### Post by nunyez on 2010-10-21
I logged in with 2d session but can't seem to modify top panel and there is no bottom panel. Am I missing something? Usually I just right click. I looked in system/appearance and searched for panel but nothing.

---

