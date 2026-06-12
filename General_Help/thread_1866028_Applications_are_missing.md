---
title: "Applications are missing"
date: 2011-10-20
forum: General Help
---

### Post by hambone79 on 2011-10-20
I just had a major crash of Unity while opening a browser window. After I restarted my computer all of the applications in the Dash menu are missing. It doesn't matter if I click Internet Apps, Media Apps, or More Apps...there is nothing there.

I have only been using Unity for a little over 3 hours now, and I'm quickly losing confidence in it.

---

### Post by hambone79 on 2011-10-21
I ran "unity --reset" and everything came back until I rebooted. Now I'm without applications again. This is pathetic.

---

### Post by hansdown on 2011-10-21
Hi, hambone79.

I think it's designed to work that way.

You can install the classic menu.

[http://www.ubuntugeek.com/how-to-install-classicmenu-indicator-on-ubuntu-11-10-oneiric-ocelot.html](http://www.ubuntugeek.com/how-to-install-classicmenu-indicator-on-ubuntu-11-10-oneiric-ocelot.html)

Log out, then back, or restart to have it on the tool bar.

---

### Post by IWantFroyo on 2011-10-21
Add the command "unity --reset" to your startup apps. It'll just run it whenever you log in.

Of course, I think they took the startup apps GUI out. I'm trying to remember the fix I used. I'll edit my post when I remember...

Edit- It seems there isn't a way to do this with commands, now that Gnome 3 is used. :evil: You'll have to try manually entering unity --reset above "exit 0" in /etc/rc.local

I'm slightly skeptical about it working, though.

---

### Post by hambone79 on 2011-10-22
I don't want to add "unity --reset" to my start up because it would take an incredibly long time to start up. Also, I have made several customizations that I would need to recreate every time I started the computer.

There has to be something wrong/missing. Everything is starting up fine, but the menus are all blank.

---

### Post by hambone79 on 2011-10-23
Ok, it is definitely a configuration problem. I deleted all of the config directories (.config, .gnome, etc.) from my user directory and then ran "unity --reset". Now everything seems to be working correctly.

---

### Post by hambone79 on 2011-11-06
Ok, this is starting to get ridiculous. I have really tried to give Unity a chance, but this problem keeps popping up at random across 2 computers which makes it extremely frustrating to use. Here is a list of things that I have tried:

1. Ran "unity --reset" but it only lasts until I reboot the computer and wipes out all of my settings.
2. Ran "sudo remove zeitgeist" and then "sudo apt-get install --reinstall unity-lens-applications unity-lens-files unity-place-applications" to try and get the menus back. Once again it only lasts until I reboot the computer but it does not wipe out my settings.
3. I have wiped out all of my settings files and directories which seems to fix the problem for several days, but it will eventually go back to blank menus.
4. Did a fresh install on my netbook and have the same problems.

Anyone have any ideas? If not I'm really going to have to consider switching to Gnome 3, KDE or something that will actually work.

---

