---
title: "Ubuntu start only command line"
date: 2011-09-20
forum: General Help
---

### Post by AMJ1992 on 2011-09-20
i have ubuntu 11.04 and installed to it gnome3 and it worked good after time i restored it back to unity and after restoring ubuntu stopped running gui only command line

---

### Post by seawolf167 on 2011-09-20
I believe that Gnome3 is still in the experimental stage, so changing from Unity to Gnome3 and back again may have broken something - do the following commands help any?

```
sudo startx
sudo service gdm restart
```

---

### Post by AMJ1992 on 2011-09-20
when i use startx or sudo startx 

it just give me  
root@ubuntu;~#  and you cant type any thing

---

### Post by psrdotcom on 2011-09-20
Can you please send us the screenshot?

---

### Post by seawolf167 on 2011-09-20
What about the other command?

```
sudo service gdm restart
```

---

### Post by AMJ1992 on 2011-09-20
using the restart code


this is the output

restart: Unknown instance:



i used this code 

sudo apt-get upgrade ubuntu-desktop

after code startx shows only blank screen

---

### Post by seawolf167 on 2011-09-20
My guess would be that changing to Gnome 3 and back again broke your system.

From the [Gnome 3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3"):
*"This package contains packages from GNOME3 and their dependencies so they can be used in Ubuntu 11.04 (Natty). This PPA is EXPERIMENTAL and MAY BREAK YOUR SYSTEM. **There is no downgrade process**."*

I'd suggest trying to reinstall your desktop completely, and if that still doesn't work, reinstalling your system. Ensure you have any necessary [backups ]("https://help.ubuntu.com/community/BackupYourSystem")before you go any further. [Clonezilla ]("http://www.clonezilla.org")is a good choice.

---

