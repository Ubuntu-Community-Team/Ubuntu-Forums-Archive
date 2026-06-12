---
title: "Using Ubuntu without GUI as default"
date: 2010-01-10
forum: General Help
---

### Post by Ibn Ar-Rashid on 2010-01-10
[FONT=Trebuchet MS][SIZE=2]Hi, I wanted to ask about how I would go about using Ubuntu without the GUI, namely, disabling it instead of removing it completely so the system boots into the console by default (like how slackware starts)? I have seen some information on this via google search on this and other forums but it seems to be either outdated or via intentionally running an error. [/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Trebuchet MS][SIZE=2] 
I want to have the system accept that I am running a CLI only session and not run errors. And as implied before, I would like to do it without simply introducing syntax errors or such in x.org files. I would also like to leave an option to start x.org whenever I want from the console as I would in slackware with the "startx" command.[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Trebuchet MS][SIZE=2] 
Furthermore, I would like to mention, I found on this and other sites a command "**sudo update-rc.d -f gdm remove**" to do this and a command "**sudo update-rc.d -f gdm defaults**" to get it back to GUI default. This seemed like what I was looking for, am I correct in my assumption? Thanx in advance.[/SIZE][/FONT]   

~

Currently using: **Ubuntu 9.10, 64-bit; dual-booted with windows 7**

---

### Post by Brandon Williams on 2010-01-10
Debian-based distros use the file /etc/X11/default-display-manager to keep track of which X11 display manager should be started. With GDM as the default, the file will contain '/usr/sbin/gdm' as its complete content. If you delete that line, leaving the file empty, gdm will not be started. This is better than the method you indicated, because /etc/X11/default-display-manager is a config file, and so the change will not be overridden by future gdm updates.

---

### Post by Ibn Ar-Rashid on 2010-01-10
Thanx, I think I will try the method you described.

---

### Post by Ibn Ar-Rashid on 2010-01-11
[SIZE=2][FONT=Trebuchet MS]I tried that method and it worked fine, thanx again for the information![/FONT][/SIZE]

---

