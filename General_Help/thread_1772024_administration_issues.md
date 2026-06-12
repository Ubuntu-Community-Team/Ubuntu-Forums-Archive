---
title: "administration issues"
date: 2011-05-31
forum: General Help
---

### Post by Messyhair42 on 2011-05-31
Over the past day or so (did a long overdue update) i've had problems when using administration tools. terminal doesn't open or close properly and the update manager might reject my root password. I can usually temporarily fix these issues with a reboot, but only for one use then the situation reverts itself to being buggy. I've been trying to finish the updates as well as clear my /tmp/ folder

---

### Post by linuxinstalledfromhdd on 2011-05-31
Try using bleachbit

sudo apt-get install bleachbit
sudo bleachbit

Careful with that as to not delete your bookmarks or passwords. 

Another great app for cleaning the system is Ubuntu Tweak package cleaner. 

And then you can try 

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean all

Just some suggestions.

---

### Post by Messyhair42 on 2011-05-31
I may not have the chance to try any of that, I rebooted once more to get terminal priviledges and the GNOME screen came up with a simpler version that wouldn't accept my password. this problem crops up every once in a while and the fix is never the same. I'm running from a USB installation right now and my first attempt will be to clear /tmp/

---

