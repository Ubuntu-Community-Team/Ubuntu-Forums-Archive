---
title: "is there a way to display video as wallpaper on desktop?"
date: 2010-03-05
forum: General Help
---

### Post by aviramof on 2010-03-05
i'v found a way to do it with screen save but not with normal video files like avi mpg and etc.

thanks in advance.

---

### Post by zine92 on 2010-03-05
I think not because normally from my experience, wallpapers must be of a image format but that doesn;t stop you from putting animating gifs.

---

### Post by lavinog on 2010-03-05
there might be a compiz plugin for it.

---

### Post by Fafler on 2010-03-05
It is possible to run mplayer in the root window, below the window manager. But i haven't ever done so with gnome, only enlightenment and xfce. I'm on a real slow internet connection right now, so i'm not gonna search for you. But look at the Electric Sheep forums. Thats what i used i for and i'm pretty sure it's explained somewhere on their forum. [http://community.electricsheep.org/](http://community.electricsheep.org/)

---

### Post by aviramof on 2010-03-05
how did you do this with enlightenment and xfce?

i have found this method for screen savers:
[http://blog.prashanthellina.com/2007/08/22/matrix-desktop/](http://blog.prashanthellina.com/2007/08/22/matrix-desktop/)

maybe there is a way to convert video to desktop or there is a screen saver that can play normal videos that i can use?

---

### Post by prshah on 2010-03-05
> **aviramof said:**
> normal video files like avi mpg and etc.


Oh yes. Check out [xwinwrap]("http://swik.net/xwinwrap"). You will need a powerful processor and graphics card to handle the load (forget about integrated Intel graphics)

It's not in the repos, but it's practically a no-brainer to install it. The usage is slightly complicated, but the examples get you started off just fine.

---

### Post by aviramof on 2010-03-05
thank you vary much i'v managed to do that by downloading shantz-xwinwrap.zip installing the deb

and then this command for example:

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet /home/****/2.avi

---

