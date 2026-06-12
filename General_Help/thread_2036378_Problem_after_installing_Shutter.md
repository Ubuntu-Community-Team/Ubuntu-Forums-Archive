---
title: "Problem after installing Shutter"
date: 2012-08-01
forum: General Help
---

### Post by alenn on 2012-08-01
I downloaded this program [http://shutter-project.org/](http://shutter-project.org/) from that site and followed instructions how to install it. when I typed sudo apt-get install shutter I had message which showed me which files need to be downloaded and installed, selected "yes" and after couple of seconds I noticed that terminal is deleting my files. I thought they are unnecessary but that all of the sudden thigs started to dissapear on my desktop and when I had nothing except wallpaper I pressed reboot button. When my PC booted again I only saw login screen and couldn't login in any of sessions I had.

Can you tell me what happend? I'm on Windows now.

---

### Post by sgoodman on 2012-08-01
maybe that shutter was in conflict with your desktop and aptitude sugested unistalls and you said yes

you can boot into console and reinstall your desktop enviroment

---

### Post by Nerdishman on 2012-08-01
can you go to a terminal by pressing ctrl-alt-f1 ?

if you can try to purge shutter and decypher the apt log and reinstall the lost, may seem like alot but it may work.

EDIT:you may need to run dpkg --configure -a if you reboted while it was running.

---

### Post by alenn on 2012-08-02
it's not only desktop deleted, I saw in messages that gnome-do is also deleted and docky, well almost everything. I will reinstall system, but I want to know what happend. Was this happend to anyone else.

---

### Post by hakermania on 2012-08-02
> **alenn said:**
> it's not only desktop deleted, I saw in messages that gnome-do is also deleted and docky, well almost everything. I will reinstall system, but I want to know what happend. Was this happend to anyone else.

No, actually nothing like this has never happened to me.
Remember to actually read the messages you get on your screen, especially when you have executed something with root privileges (sudo command).

Why didn't you download shutter from the Ubuntu Software Center?

---

