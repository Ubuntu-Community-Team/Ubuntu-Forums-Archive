---
title: "Problems after installing 9.04"
date: 2010-07-09
forum: General Help
---

### Post by Brisman on 2010-07-09
Hey. I recently tried to upgrade to 10.04 but during the upgrade my powerpack failed. Now 10.04 has been installed but I cannot acess Synaptic through the drop down menu it says "Unable to get an exclusive lock"

I've tried accessing it through Terminal which works but then the only option I have is to Partial Upgrade but then that freezes at the first stage saying the old database can't access the new (or something along those lines) then that screen just remains there.

Also when I minimise any windows I have open they don't appear at the bottom of the screen I have to go to multi screen to find them. Any kind of help would be tremendous. 
Thanks

---

### Post by Darkness Des on 2010-07-09
Have you considered reinstalling? I mean, if your power went off sometime while it was doing that, it's very likely your install is corrupted. dpkg (base package manager) is most likely corrupted. Do a clean install, that's all I can offer. Unless it's really a SIMPLE problem. Try running this command from the terminal (Applications -> Accessories -> Terminal):
```
killall dpkg
```
and then try opening Synaptic again. Synaptic will be closed too if it is open during this process. This command can't do any harm if nothing is wrong with that. The effects of the command are gone upon logout. So run that first, then tell me if it works.

---

### Post by Brisman on 2010-07-09
All I get after trying that is 
dpkg: no process found

I have also tried '-release-upgrade' but that has done nothing as well

---

### Post by Darkness Des on 2010-07-10
Alright. It just occurred to me that dpkg wouldn't be running anyways. Try running
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
in the terminal. It will ask for your password on the first command (or on each command, depends on how long each takes). When you enter it, you won't see any dots or stars to show that you put it in. But believe me, it's there. Just push enter after you typed it and you're on your way. That should update your system to the latest version. It should also install and fix corrupt packages.

---

