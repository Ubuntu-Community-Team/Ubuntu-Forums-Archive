---
title: "professional  looking distro"
date: 2011-08-03
forum: General Help
---

### Post by techfighterminal on 2011-08-03
Hey guys, I'm looking for a new distro to try, preferably debian/ubuntu based. but i'm hoping there's one out there with a black, hacker, or pro look to it. not kiddy looking. (like Debian's lil rockets)mainly i would like the boot up, and login screen, as i don't know how to change these.. 

alternatively if someone has a guide to change these that would also help..

---

### Post by Kira_Belka on 2011-08-03
backtrack 4)))

---

### Post by techfighterminal on 2011-08-03
> **Kira_Belka said:**
> backtrack 4)))


i thought backtrack was a legitimate hacking distro? i'm not really at a pro level, i just want it look pro.

---

### Post by knutschr on 2011-08-03
Here you can change Ubuntu to a black look.
[http://ubuntusatanic.org/news/](http://ubuntusatanic.org/news/)

---

### Post by techfighterminal on 2011-08-03
> **knutschr said:**
> Here you can change Ubuntu to a black look.
[http://ubuntusatanic.org/news/](http://ubuntusatanic.org/news/)


this is a satanic look, i mean like IT professional, hacker look. is it possible for me to change my boot screen, and such?

---

### Post by tommpogg on 2011-08-03
You can customise your own Ubuntu. Take a look [here]("http://gnome-look.org/")

---

### Post by ajgreeny on 2011-08-03
You can do most of that I think in ubuntu.

Firstly remove the words **quiet** **splash** from the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```line in /etc/default/grub, leaving the empty "",  and you will get a full text boot.  I can't remember if it removes the plymouth screen as well (the purple background with word "ubuntu" and the five animated dots) but if not you can use a different plymouth theme.

Secondly if you don't want wallpaper on the desktop you don't have to use anything, just have a black overall colour instead.

Alternately you could always install the minimal install CD of ubuntu, or the server edition, to which you can add whatever packages you want;  you don't even have to add x-server if you don't want it but can manage with just a text output.

---

### Post by Kira_Belka on 2011-08-03
mb just matrix-wallpaper?) ... ubuntusatanic 's good idea)) lol)

---

### Post by Wim Sturkenboom on 2011-08-03
You can try CrunchBang; black by default :D.

Based on Debian nowadays.

---

