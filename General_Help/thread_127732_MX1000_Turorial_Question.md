---
title: "MX1000 Turorial Question"
date: 2006-02-09
forum: General Help
---

### Post by Zach1188 on 2006-02-09
I read the tutorial at [https://wiki.kubuntu.com/MX1000Mouse](https://wiki.kubuntu.com/MX1000Mouse) and I am having some troubles.

In the "Set up xbindkeys" section, I type gedit ~/.xbindkeysrc in the terminal, and it says "bash: gedit: command not found". I followed all the directions exactly and successfully up to this point.

Then it says:
> 
Save your changes and exit.

Add xbindkeys to your startup programs in the System -> Preferences -> Sessions -> Startup Programs

Well, where is System -> Preferences -> Sessions -> Startup Programs? I go to the K menu, go to system, but where is prefrences? Then I try to go to the prefrences menu (The one outside of the system menu), and Startup Programs is not there?

---

### Post by Zach1188 on 2006-02-09
I hate to do it, but... bump.

---

### Post by FlakJacket on 2006-02-09
try using nano instead of gedit (gedit is gnome) and i'll take a look for the startup programs.

Flak

EDIT: i think i found it /home/user/.kde/Autostart/            You should be able to just put a shortcut there

---

### Post by Zach1188 on 2006-02-09
Thanks for the help, I got my back/forward buttons working. I just need to figure out how to make it begin at startup (Thanks for looking).

---

### Post by jrib on 2006-02-09
hi, do one of you mind updating the tutorial and adding those startup instructions for kde?  I would do it myself, but don't use kde...  Thanks :D

---

### Post by FlakJacket on 2006-02-09
Yeah that tutorial is for GNOME so you have to change things here and there.

EDIT: _jason I don't want to create a launchpad account tonight so maybe another time.

---

### Post by Zach1188 on 2006-02-09
I assumed it was for Kubuntu because the URL is [https://wiki](https://wiki).**kubuntu**.com/MX1000Mouse

Well then, where is the startup program settings in KDE?

---

### Post by jrib on 2006-02-09
[QUOTE=Zach1188]I assumed it was for Kubuntu because the URL is [https://wiki](https://wiki).**kubuntu**.com/MX1000Mouse

Well then, where is the startup program settings in KDE?[/QUOTE]

wiki.kubuntu.com is apparently the same wiki as wiki.ubuntu.com except with a different style sheet.  I didn't know that either until just now

---

### Post by FlakJacket on 2006-02-09
read my above edited post: /home/user/.kde/Autostart/

---

