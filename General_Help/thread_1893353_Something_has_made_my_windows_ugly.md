---
title: "Something has made my windows ugly"
date: 2011-12-10
forum: General Help
---

### Post by TennSeven on 2011-12-10
Hi all,

I am on 11.10 and earlier today I ran apt-get upgrade, which upgraded a ton of packages (too many for me to wind through).  The problem is that it somehow changed the look of gnome so now my nautilus windows look a lot less appealing.  The change is most evident in the bookmarks list on the left side and also in the folder buttons (circled in the screenshots below).  Can someone tell me where I need to go to change it back to the way it was? I am running gnome-classic.

-TennSeven

Here is what my Nautilus windows look like now:
[[IMG]http://img825.imageshack.us/img825/9316/screenshotte.th.png[/IMG]](http://imageshack.us/photo/my-images/825/screenshotte.png/)

Here is what my Nautilus windows used to look like:
[[IMG]http://img6.imageshack.us/img6/4411/correctj.th.png[/IMG]](http://imageshack.us/photo/my-images/6/correctj.png/)

---

### Post by Viman on 2011-12-10
It happens to me as well, from time to time... at first I got scared because I thought something caused the Root configurations to apply to my local settings, but it went away after I logged out and logged in.

have you tried rebboting/logging in again? It may go away... from my experience this is nothing, really.

---

### Post by BC59 on 2011-12-10
I found this from many years ago but it could help. It's applying the opposite so just improvise:

@Artificial Intelligence

Are you tired of that your root applications doesn't match your desktop theme?

Here's the answer, this show with the D3a GTK2 theme. Just change D3a with your favorite GTK theme:

cd /home/orion/.themes
sudo cp -r d3a /usr/share/themes
[COLOR="Blue"]gk[/COLOR]sudo gedit /etc/gdm/gdm.conf

Now I changed under [gui]

GtkTheme=d3a
GtkThemesToAllow=d3a

---

### Post by stinkeye on 2011-12-10
Happens to me a lot.
Easy fix...restart nautilus.
In the terminal
```
nautilus -q
```

---

### Post by Spyderkid on 2011-12-10
If it happens to the desktop and icon theme in general run

sudo apt-get --reinstall instal light-dm

---

### Post by TennSeven on 2011-12-13
Thanks Stinkeye, restart fixed it!

---

