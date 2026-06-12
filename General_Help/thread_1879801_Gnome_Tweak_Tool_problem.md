---
title: "Gnome Tweak Tool problem"
date: 2011-11-12
forum: General Help
---

### Post by Raven777 on 2011-11-12
I'm using Ubuntu 11.10 and I've installed Gnome Tweak Tool but I can't find it in my programs list. Where do I need to go after installing it?

---

### Post by BillyBoa on 2011-11-12
Open the Dash (upper left icon) in the Search dialogue write "Advanced Settings".

It's the Gnome Tweak Tool

---

### Post by raja.genupula on 2011-11-12
> **Raven777 said:**
> I'm using Ubuntu 11.10 and I've installed Gnome Tweak Tool but I can't find it in my programs list. Where do I need to go after installing it?

[http://www.webupd8.org/2011/06/gnome-tweak-tool-305-lets-you-install.html](http://www.webupd8.org/2011/06/gnome-tweak-tool-305-lets-you-install.html)

EDIT: watch last lines

---

### Post by Raven777 on 2011-11-12
I've definitely installed it correctly but there is no "Gnome tweak tool" option in my home folder. I also can't use dash because I'm not using Unity.

---

### Post by vasa1 on 2011-11-12
> **Raven777 said:**
> I've definitely installed it correctly but there is no "Gnome tweak tool" option in my home folder. I also can't use dash because I'm not using Unity.

Run this code:
```
dpkg --get-selections > installed-software
```

It will create a text file called "installed-software" in your current directory and it will list your installed software.

You should see it like this:
```
gnome-themes-standard				install
gnome-themes-ubuntu				install
gnome-tweak-tool				install
gnome-user-guide				install
gnome-user-share				install
gnome-utils-common				install

```

---

### Post by Frogs Hair on 2011-11-12
Enter your search as BillyBoa suggested . If you can't open it logout and back in and try again .

---

