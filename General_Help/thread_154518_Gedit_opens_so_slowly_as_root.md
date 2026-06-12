---
title: "Gedit opens so slowly as root"
date: 2006-04-03
forum: General Help
---

### Post by Dafydd on 2006-04-03
Don't know what's happened but gedit, cream, bluefish etc all open soooooo slowly when I open a root terminal. Does anyone have any suggestions what to do? Googling hasn't helped.

nano opens quickly but doesn't allow me t ctrl+c/v etc...

dafydd

---

### Post by aysiu on 2006-04-03
Are you doing this? ```
su
gedt filename
``` or this? ```
sudo gedit filename
``` or this? ```
gksudo gedit filename
```

---

### Post by Dafydd on 2006-04-03
[QUOTE=aysiu]Are you doing this? ```
su
gedt filename
``` or this? ```
sudo gedit filename
``` or this? ```
gksudo gedit filename
```[/QUOTE]

Hi! I've tried all of the above. In fact, any program run as root from the terminal takes so long to open (3-5 mins). It's strange as gedit or nautilus open fine if I just use the normal menu and open them as a normal user.

Any help would be well appreciated!

Dafydd

---

