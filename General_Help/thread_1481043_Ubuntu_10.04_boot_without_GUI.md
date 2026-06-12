---
title: "Ubuntu 10.04 boot without GUI"
date: 2010-05-12
forum: General Help
---

### Post by ivan.eggel on 2010-05-12
Hi All

I've installed ubuntu 10.04, basically im using the machine as a server (but not only) and i'd like that it boots into text mode without GUI, so i can directly login into the console. But i want to be able to start X from the console later (startx). How can i do that with Ubuntu 10.04? Is there a way without too many workarounds?

Thanks for your help
-Ivan

---

### Post by mkvnmtr on 2010-05-12
Before 10.04 it was easy to just uninstall GDM and have a command line log in. I do not believe you can do t in 10.04. You might try a server install and then add xorg and something like xfce4 to get a desktop. Try it on an empty partition or in virtual box to get it like you want before you change anything on a working system.

---

### Post by ivan.eggel on 2010-05-14
Ok thanks for your answer. Im just wondering why they have no easy way to enable booting without GUI. It's strange. Well uninstalling GDM? No...i want to use gnome..but i just want to start it after typing startx in the console-mode. And i do not want to switch to ubuntu server, because the system is working really good now, so dont want to reinstall everything.

Any other hints?

Thanks

---

### Post by ShiftyEyes on 2010-05-15
I do the same thing. My method is:

1. sudo nano /etc/X11/default-display-manager
2. Remove the line: '/usr/sbin/gdm'
3. The boot-up screen just indefinitely displays the ubuntu logo, so a couple seconds after booting I hit alt + F1 to get to a command-line login.
4. To start gnome after logging in from the console, type 'sudo gdm'

If anyone knows how to avoid step 3 and have it go directly to the command-line login, I would greatly appreciate it. Under 9.10 and earlier I didn't have this problem, but it's such a minor thing that it's okay if it can't be fixed.

---

### Post by foe83 on 2010-05-24
I'm also interested in this, isn't there a way perhaps to create a grub2 entry which loads to run level 3? I'm not really knowledgeable about this, but if I understand it correctly, this should be what we want to achieve!

---

### Post by frieze on 2010-06-07
They moved the gdm start from init.d to the upstart system. go to /etc/init and rename gdm.conf to gdm.DONOTSTART. All credit to the IRC chan.

---

