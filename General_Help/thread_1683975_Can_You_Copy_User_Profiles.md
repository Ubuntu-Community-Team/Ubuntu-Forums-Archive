---
title: "Can You Copy User Profiles?"
date: 2011-02-08
forum: General Help
---

### Post by Muhnamana on 2011-02-08
So I originally setup 1 user on my Ubuntu 10.10 machine, Username1.

I've now added a Username2. It is possible to copy the profile and settings of Username1 and use it with Username2?

If so, how can I go about doing so.

Any help is appreciated.

Thanks!

---

### Post by techunit on 2011-02-08
not sure you could try copying you home folder over to the new user profile. good luck. make sure you get the hidden files.

---

### Post by randiroo76073 on 2011-02-08
Yes, you can, the easiest way(for me) is to open a terminal and enter: 
```
 sudo nautilus 
```
enter your password, this will open nautilus in root mode and make the transfer easier, especially on all hidden files. I don't transfer the whole contents of /home/user, only the needed files. But if you're new to Ubuntu it would be easier for you to just transfer all. Be aware that you will get popups asking if you want to overwrite files, the answer will be yes or ok.
I've been doing it this way for several years and haven't had a prob yet.

---

### Post by Krytarik on 2011-02-08
You have to take of the ownerships after you copied the profile. I'd do it like this:
- logout
- switch to a console by pressing Alt+Ctrl+F1
- login with "username1"
```
sudo mv /home/username2 /home/username2-backup
sudo cp -a /home/username1 /home/username2
sudo chown username2.username2 -R /home/username2
```- logout
- press Alt+Ctrl+F7 or F8 to switch to GDM again

---

### Post by Krytarik on 2011-02-08
> **randiroo76073 said:**
> 
```
 sudo nautilus 
```
Advice: Don't use "sudo" for graphical apps, use "gksudo" instead.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Muhnamana on 2011-02-10
Thanks guys. I'm still fairly new to Ubuntu, so hopefully this is idiot proof!

---

