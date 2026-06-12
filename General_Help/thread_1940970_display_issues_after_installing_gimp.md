---
title: "display issues after installing gimp"
date: 2012-03-14
forum: General Help
---

### Post by zaiger on 2012-03-14
Hello,

a better title would probably be: "messed up my display after installing unknown PPAs linked from gimp 2.7 prerelease LP"

So I tried to install gimp 2.7 from PPA from  [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn")

I installed it but it didn't work, GIMP installed but wouldn't open, so I read on the launchpad page:

> GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos
 deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main
 deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main
I apt-updated and upgraded and from then on I am having major problems with my display. It seems to only effect system-related things like the software centre and GTK and not Firefox, which is why I can write this.

I removed the PPA's and had a difficult time as you can see it wasn't easy. [http://i.imgur.com/iF0Ka.png](http://i.imgur.com/iF0Ka.png)
I finally got them by moving the scrollbar (when it would show up) juuuuust enough to see the last 3 or 4 letters.

Anyways, that is how my computer looks now, I can't see any system menus, search bars are blacked out. I don't know what to do. Can anyone help me?

Another screenshot [http://i.imgur.com/gAm8l.png](http://i.imgur.com/gAm8l.png), my bookmarks go all the way down, but here they have vanished.

Edit: [http://i.imgur.com/oD5xV.png](http://i.imgur.com/oD5xV.png) idk what's going on D:

---

### Post by zaiger on 2012-03-14
I don't really know where to start troubleshooting.

Anyone have any ideas? Should I just set my laptop on fire and go buy a macbook, or is it something that might be fixable?

Edit: Decided to back-up and reinstall: [http://i.imgur.com/Bn6zY.jpg](http://i.imgur.com/Bn6zY.jpg)

---

### Post by zaiger on 2012-03-15
bump

Nobody has any theories as to what could resolve these visual errors?

---

### Post by |{urse on 2012-03-15
Well if you screwed up glibc, that's an uh-oh.

Try installing a different DE yet? gnome-shell or lxde perhaps.

---

### Post by |{urse on 2012-03-15
Also, of course, try disabling and removing the ppa repo and package and install the latest stable gimp in the official repos.

---

### Post by zaiger on 2012-03-15
I just reimaged the whole partition. I installed gnome-shell and it was the same. The problem was GTK not Unity. Thanks for the suggestions though :)

---

### Post by |{urse on 2012-03-16
well, glad you got it sorted :guitar:

---

