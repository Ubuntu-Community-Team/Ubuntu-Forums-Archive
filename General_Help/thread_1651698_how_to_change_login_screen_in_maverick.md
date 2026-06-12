---
title: "how to change login screen in maverick?"
date: 2010-12-23
forum: General Help
---

### Post by vagrantjoe on 2010-12-23
this was the instruction given...

Use 'gdmsetup' to install.

But when I open my so called "gdmsetup" or log in screen from system - admin all I find is...

playing sound 
show list of users
show screen for choosing who will log in
login as automatically
select default session

kindly help

---

### Post by cariboo on 2010-12-24
The only thing you can change is the wallpaper, nothing else is user configurable.

---

### Post by vagrantjoe on 2010-12-24
tan q mr ubuntu staff... you guys rock... awesome.... legen (wait for it) dary....

---

### Post by Verbeck on 2010-12-24
you could change it to another gtk theme/colour/icon etc..
from a terminal run
```

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```then logout and change the theme/colours/font and login
after that, enter
```

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

```

[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

---

### Post by vagrantjoe on 2010-12-24
thanks verberk...

---

