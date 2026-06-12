---
title: "Can't Login into ubuntu 11.10"
date: 2011-11-29
forum: General Help
---

### Post by Tadcrazio on 2011-11-29
So for about a week or so I have been using 11.10 with the gnome shell. No problem, a couple days ago i got KDE and was fooling around with that. I woke up today opened my laptop continued my suspended session and it was slow, so i restarted. Upon rebooting I no longer can login to ubuntu or kubuntu or anything else. I type in my username and password and the box disappears and comes right back to the login screen.


I tried doing:
cntrl + Alt + F1
login name/password
ls -shla |grep "Xauthority"
sudo mv .Xauthority Xauthority.old
Sudo shutdown -r now


It appears that it moved Xauthority but it didn't fix my problem. Hopefully someone else can ?

---

