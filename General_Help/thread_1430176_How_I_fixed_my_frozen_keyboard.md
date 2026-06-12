---
title: "How I fixed my frozen keyboard"
date: 2010-03-15
forum: General Help
---

### Post by hart02 on 2010-03-15
Some people have had issues with their keyboard being frozen at login. I was one of those people until I discover a workaround. Here is how I managed to fix it for me:

First when I get to the login screen which is frozen I press and hold **Alt+PrintScrn**
Then I press **R+E** which takes me to the console and login as my user
Next I type **sudo service dbus force-reload**
After that I type **sudo gdm**
I Finally select my user,then I press a key and It's alive NumLock and all.
I have tried this with wdm and it didn't work for me. I am not sure about other login managers working but I will stick with gdm. Also I removed the packages xorg and ubuntu-desktop so you should test this technique with those installed. I am using lxde as my desktop.Now if only someone could automate this with an init.d script.:KS

---

