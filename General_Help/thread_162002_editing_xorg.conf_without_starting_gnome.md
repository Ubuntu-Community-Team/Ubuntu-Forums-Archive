---
title: "editing xorg.conf without starting gnome"
date: 2006-04-18
forum: General Help
---

### Post by hikitsu4 on 2006-04-18
Hello i need some help with editing xorg.conf i made some mistakes when editing it and i cannot start gnome it just jumps me out to the command prompt.

I know what to edit to fix it i just need some help with some editing tool to edit without using gnome (using the command prompt). 

I tried "vim" but i could not get it to save and i could not exit it becourse it is so hard to use. So if anybody know a easier program, or how you save and exit with "vim" that would help alot.

---

### Post by Sutekh on 2006-04-18
I would use 'nano' you should find it quite easy to use.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
To save use Ctrl+O and to exit use Ctrl+X.

---

### Post by krismatth3 on 2006-04-18
To save with vim, press Escape then type ":w" and press enter. To exit, press Escape and then type ":q" and hit return. If vim complains that the file has not been saved and won't let you exit (and you don't want to save!), press Escape and then type ":q!" and hit return.

---

### Post by niviche on 2006-04-18
What can greatly help to edit Xorg.conf is the ability to edit it from Windows (if you are dual booting). This [free driver](http://www.fs-driver.org/download.html) works wonder for this, letting you see your Linux partition from XP.

---

### Post by hikitsu4 on 2006-04-18
thanks for all the help i fixed it and it works now.

---

