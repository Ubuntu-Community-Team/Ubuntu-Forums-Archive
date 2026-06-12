---
title: "installing XWinWrap"
date: 2009-07-19
forum: General Help
---

### Post by sidious1741 on 2009-07-19
I wanted to try an animated wallpaper.  I found [http://www.gnome-look.org/content/show.php/Animated+Desktop+(With+XWINWRAP)?content=104598]("http://www.gnome-look.org/content/show.php/Animated+Desktop+(With+XWINWRAP)?content=104598") which says
> How to install xwinwrap:
sudo apt-get install xorg-dev build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cd xwinwrap
make
sudo ln -s /usr/src/xwinwrap/xwinwrap /usr/bin/

The ":p" is ":\p" without the "\"

However, when I type in cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap I get
```
timothy@timothy-desktop:~$ cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cvs checkout: CVS password file /home/timothy/.cvspass does not exist - creating a new file
cvs [checkout aborted]: reading from server: Connection reset by peer
```

---

### Post by sidious1741 on 2009-07-20
So instead of cvs I found a package at [http://tombuntu.com/index.php/2008/12/15/animated-wallpaper-on-your-ubuntu-810-desktop/]("http://tombuntu.com/index.php/2008/12/15/animated-wallpaper-on-your-ubuntu-810-desktop/")  But now, I guess I just have a problem with my graphics card.  I have a cheap Intel card that came with the comp.  When I ran the thing, the screen began flashing violently and I could not control my windows.  ctrl-alt-F1 didn't work either.  So can I be sure that the problem is with the graphics card?

---

