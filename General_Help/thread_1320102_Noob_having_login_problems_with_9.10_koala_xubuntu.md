---
title: "Noob having login problems with 9.10 koala xubuntu"
date: 2009-11-08
forum: General Help
---

### Post by emanruson on 2009-11-08
Hello

I foolishly upgraded my system from 9.04 xubuntu to 9.10 koala xubuntu, now I have problems which I did not have before.

The system rarely allows me to login, when I attempt to login the CRT screen blinks and clicks a few times, then goes back to the buzzing bugs, then goes back to the beginning of the login process. It takes me dozens and dozens of attempts before I can login.

I have been trying different things to try and fix it. The hitting esc at system boot then using the auto repair options wont fix it. I can login using xterm or gnome sessions but not xfce session. So I am guessing the problem is with xfce?

As well as the login problem the system has recently started randomly rebooting itself, which of course makes the login problem even more annoying. Generally I leave the system running 24/7 with the main load being a copy of alt.binz running under wine and a copy of pan also running.

I dont want to do a fresh install because of the amount of time it would waste and the possibility of data loss. I cant use xterm because I simply dont have the skill to work without a gui. And, I would rather not use gnome because it defeats the purpose of installing xubuntu rather than plain ubuntu (which was to make the best use of my poor equipment, which was all I could afford).

Has anyone heard of this login problem in Xub?

And, more importantly does anyone know of a solution?

Can I ¨roll back¨ the upgrade from 9.10 koala to 9.04, without doing a reinstall?


Here is some info on my system:

ubuntu
release 9.10 (karmic)
Kernel Linux 2.6.31-14-generic
gnome 2.28.1

hardware
memory 2.0 Gib
Processor Intel Celeron CPU 2.40GHz

system status
available disk space 370.1 GiB

Xfce 4 Desktop Environment
version 4.6.1 (Xfce 4.6)

Xfce is a collection of programs that together provide a full-featured
desktop environment. The following programs are part of Xfce:

o Window manager (xfwm4)
   handles the placement of windows on the screen

o Panel (xfce4-panel)
   program launchers, popup menus, clock, desktop switcher and more

o Desktop manager (xfdesktop)
   sets a background color or image and provides a menu when you click on
   the desktop background

o File manager (thunar)
   fast file manager

o Session manager (xfce4-session)
   restores your session on startup and allows you to shutdown the computer
   from Xfce

o Utilities
   xfprint4: print files
   xfrun4: run programs


Xfce 4 is also a development platform providing several libraries, that help
programmers create applications that fit in well with the desktop environment.

Xfce 4 components are licensed under free or open source licences, GPL or BSDL
for applications and LGPL or BSDL for libraries. Look at the documentation,
the source code or the xfce website ([http://www.xfce.org](http://www.xfce.org)) for more
information.


Help please.

Thank you


Emanruson

---

### Post by peyre on 2009-11-09
I'm having similar problems, also since I upgraded from 9.04 to 9.10.  I select my account (OR select Other and enter my user name), then enter my password...it does exactly what you describe, going back to the login screen like I fat-fingered my password.  It usually accepts my credentials after 2-4 login attempts, though.

---

### Post by PendoLeMellon on 2009-11-15
I have the same login problem and made a post about it in this thread:

**Login problems after upgrading to 9.10**
[http://ubuntuforums.org/showthread.php?p=8321494](http://ubuntuforums.org/showthread.php?p=8321494)

The problem arises when I change the desktop resolution.

---

### Post by peyre on 2009-11-15
I found a workaround for this issue.  It worked for me, anyway.  Can't remember where I saw it, but here's the workaround.

[LIST]
[*]Switch to a text console by pressing Ctrl-Alt-F1
[*]Log in at the text prompt
[*]Navigate to $HOME/.config/xfce4/xfconf/xfce-perchannel-xml
[*]In that folder, delete displays.xml (enter rm displays.xml)
[*]Log out of the text console and switch back to the graphical login screen (or reboot (sudo reboot), which is what I did)
[/LIST]
If there is no displays.xml file inside xfce-perchannel-xml, you could try going back to $HOME and deleting the whole .config folder (rm -r .config).  I saw that recommended _[here]("http://ohioloco.ubuntuforums.org/showthread.php?t=1310069")_, though it didn't work for me when I tried it.

---

### Post by PendoLeMellon on 2009-11-23
I found a solution.

Go to *Applications > System > Updates. *Click on* Preferences* and enable *"pre-released updates (karmic-proposed)"*.

Run the update procedure at least once, and then disable the pre-release updates again, as some of them might be a little bit unstable. I'm sure an official update will be released soon also.

---

### Post by peyre on 2009-12-01
That's great PendoLeMellon, but how are we to do that when we can't log in to X in the first place?

---

