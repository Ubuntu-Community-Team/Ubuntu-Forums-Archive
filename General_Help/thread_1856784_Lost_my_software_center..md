---
title: "Lost my software center."
date: 2011-10-09
forum: General Help
---

### Post by creata.physics on 2011-10-09
So I was trying to install gnome 3.2 ( which was an epic fail ).

Anyway, I had issues with the install, tried to revert back, encountered a bunch of issues.

Anyway, I have gotten everything fixed so, so I think, except for one last thing I'm missing, the software center.

I tried to see if apt-get install software-center would do anything, but it is just trying to install humanity theme packs.

Alright, so what I need to know is if it's possible to install my software center from apt-get? If so what's the exact command.

Thanks,
Matt

---

### Post by WasMeHere on 2011-10-09
> **creata.physics said:**
> So I was trying to install gnome 3.2 ( which was an epic fail ).

Anyway, I had issues with the install, tried to revert back, encountered a bunch of issues.

Anyway, I have gotten everything fixed so, so I think, except for one last thing I'm missing, the software center.

I tried to see if [COLOR="Red"]apt-get install software-center[/COLOR] would do anything, but it is just trying to install humanity theme packs.

Alright, so what I need to know is if it's possible to install my software center from apt-get? If so what's the exact command.

Thanks,
Matt
When I run *software-center* in a terminal window it launches the program that I think you want. As far as I understand, it is the correct command except that your need root privileges, so try again with *sudo*:
```
sudo apt-get install software-center
```
Have fun
Olle

---

### Post by creata.physics on 2011-10-09
When I ran sudo apt-get install software-center, I get this:
```

matthew@matthew-Dimension-3000:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  humanity-icon-theme
The following NEW packages will be installed:
  humanity-icon-theme software-center
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.

```

I guess I missed, software-center after the humanity-icon-theme so it was there the whole time, just a mess up on my part.

I guess I'll need to create another topic for also losing the feature of locking my screen.

---

### Post by Krytarik on 2011-10-09
> **creata.physics said:**
> I guess I'll need to create another topic for also losing the feature of locking my screen.
Try running this first:
```
sudo apt-get install ubuntu-desktop
```
If it tells you that it's already installed, go on.

Regards.

---

### Post by Off Topic on 2011-10-09
sudo apt-get install gnome-app-install

---

### Post by creata.physics on 2011-10-09
sudo apt-get install ubuntu-desktop
worked perfect, thanks a bunch.

---

