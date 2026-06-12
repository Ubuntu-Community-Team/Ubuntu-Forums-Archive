---
title: "Getting ç cedilla instead of c acute with american keyboards"
date: 2009-11-18
forum: General Help
---

### Post by leorolla on 2009-11-18
To get a ç we need to press "AltGr" + "," which is **horrible** if you need ç very often.

We want "acute then c" back, which is the standard behavior in other OS's and is far better.

[COLOR=Red]      '+c = ç !!!
[/COLOR]
[B]We don't want to change the language or the locale settings, we just want a Ç !!!
[/B]
Below is a solution for Ubuntu with Gnome Desktop.
It doesn't work for KDE applications, though.
For KDE applications see the next post.

It is a shame that we need all that everytime we use Ubuntu on a different computer.

There is an idea of having this fixed, so if this also annoyes you, there is a voting going on:
[http://brainstorm.ubuntu.com/idea/7603/](http://brainstorm.ubuntu.com/idea/7603/)

________

I have tested on an american laptop with Ubuntu 9.10, but the procedure should work with other distros:

```
sudo cp /etc/X11/xinit/xinput.d/none /etc/X11/xinit/xinput.d/none-backup$RANDOM
sudo gedit /etc/X11/xinit/xinput.d/none

```(may be none.conf)

```
GTK_IM_MODULE=gtk-im-cedilla

``````
sudo gedit /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules

```(in older distros it was /etc/gtk2.0/gtk.immodules)

```
- "cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa"
+ "cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa:en"

```
Credits:
[http://ubuntuforums.org/showpost.php?p=8157623&postcount=11](http://ubuntuforums.org/showpost.php?p=8157623&postcount=11)
[http://www.fedora.org.br/post38423.html](http://www.fedora.org.br/post38423.html)
[http://havratips.blogspot.com/2007/06/cedilla-cedilha-problem-to.html](http://havratips.blogspot.com/2007/06/cedilla-cedilha-problem-to.html)

---

### Post by leorolla on 2010-02-04
The above solution is good for Gnome Desktop and GTK-based applications.

For Qt and KDE-based applications, do the following:

```
cd /usr/share/X11/locale/$LANG
sudo cp Compose Compose-backup
sudo gedit Compose

```then search and replace "&#263;" by "ç" and  "&#262;" by "Ç".

Credits:
[http://art.ubuntuforums.org/showpost.php?p=4247647&postcount=27](http://art.ubuntuforums.org/showpost.php?p=4247647&postcount=27)

---

### Post by leorolla on 2010-06-07
To have cedilla without sudo:
```
echo export GTK_IM_MODULE=cedilla >> ~/.env
```
Log out, log in, voilà!

It works even when you are just a user, and it survives GTK updates.

Obvious drawback: must do it for each user.

---

### Post by cipricus on 2013-04-15
In Xfce Quantal (Xubuntu 12.10 / Linux Mint 14 Xfce) install the `ibus` package and its dependencies.

---

### Post by overdrank on 2013-04-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

