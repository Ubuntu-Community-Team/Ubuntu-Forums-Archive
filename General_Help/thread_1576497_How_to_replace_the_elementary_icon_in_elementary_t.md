---
title: "How to replace the elementary icon in elementary theme"
date: 2010-09-17
forum: General Help
---

### Post by gauravbutola on 2010-09-17
How to replace the elementary icon in elementary theme. I am sure it's possible. 
I installed the elementary theme but whenever I switch to elementary theme from ambience, the Ubuntu logo beside applications on the left upper corner of the screen changes into e of elementary logo.

Attaching a screenshot.

[IMG]http://i.imgur.com/McDe9.jpg[/IMG]

thanks
Gaurav Butola

---

### Post by gauravbutola on 2010-09-17
Bump

---

### Post by gauravbutola on 2010-09-18
bump

---

### Post by TeutonJon78 on 2010-10-19
I'm not sure how to do it directly or from the command line (other than replace the graphic file in the theme), but Ubuntu Tweak lets you do this pretty easily.  You can replace it with any png or svg you'd like.

---

### Post by PJSingh5000 on 2010-10-30
Gaurav,


_TO CHANGE THE ICON_

(1) Make a backup of the original "e" icons...

```

$ cd /usr/share/icons

$ sudo mv ./elementary/places/22/start-here.svg ./elementary/places/22/start-here.svg.original
$ sudo mv ./elementary/places/48/start-here.svg ./elementary/places/48/start-here.svg.original
$ sudo mv ./elementary/places/24/start-here.svg ./elementary/places/24/start-here.svg.original
$ sudo mv ./elementary/places/64/start-here.svg ./elementary/places/64/start-here.svg.original
$ sudo mv ./elementary/places/24/distributor-logo.svg ./elementary/places/24/distributor-logo.svg.original

```

(2) Copy the "Ubuntu" Humanity icons into the elementary theme.

```

$ cd /usr/share/icons

$ sudo cp ./Humanity/places/22/start-here.svg ./elementary/places/22/start-here.svg
$ sudo cp ./Humanity/places/48/start-here.svg ./elementary/places/48/start-here.svg
$ sudo cp ./Humanity/places/24/start-here.svg ./elementary/places/24/start-here.svg
$ sudo cp ./Humanity/places/64/start-here.svg ./elementary/places/64/start-here.svg
$ sudo cp ./icons/Humanity/places/24/distributor-logo.svg ./elementary/places/24/distributor-logo.svg

```

(3) Log-out and log-in again.



_TO UNDO (REVERT) THE ICON CHANGE_

(1) If you want to undo this change, simply replace the copied icons with your back-up of the "e" icons...

```

$ cd /usr/share/icons
$ sudo mv ./elementary/places/22/start-here.svg.original ./elementary/places/22/start-here.svg
$ sudo mv ./elementary/places/48/start-here.svg.original ./elementary/places/48/start-here.svg
$ sudo mv ./elementary/places/24/start-here.svg.original ./elementary/places/24/start-here.svg
$ sudo mv ./elementary/places/64/start-here.svg.original ./elementary/places/64/start-here.svg
$ sudo mv ./elementary/places/24/distributor-logo.svg.original ./elementary/places/24/distributor-logo.svg

```

(2) Log-out and log-in again.

---

### Post by PJSingh5000 on 2011-09-24
Since the previous steps no longer work for Ubuntu 11.04, here is an update.  This works for Ubuntu 11.04 ("Natty") using the Elementary icons from the elementaryart ppa repository (for "Maverick"). I tested this using the "Classic" desktop environment rather than Unity.

_TO CHANGE THE ICON_

Make a backup of the original "e" icons and link to the corresponding "Ubuntu" icons...

```
sudo mv /usr/share/icons/elementary/panel/22/start-here.svg /usr/share/icons/elementary/panel/22/start-here.svg.original
sudo ln -s /usr/share/icons/Humanity/places/22/start-here.svg /usr/share/icons/elementary/panel/22/start-here.svg

sudo mv /usr/share/icons/elementary/panel/24/start-here.svg /usr/share/icons/elementary/panel/24/start-here.svg.original
sudo ln -s /usr/share/icons/Humanity/places/24/start-here.svg /usr/share/icons/elementary/panel/24/start-here.svg

sudo mv /usr/share/icons/elementary/places/24/distributor-logo.svg /usr/share/icons/elementary/places/24/distributor-logo.svg.original
sudo ln -s /usr/share/icons/Humanity/places/24/distributor-logo.svg /usr/share/icons/elementary/places/24/distributor-logo.svg

sudo mv /usr/share/icons/elementary/places/48/distributor-logo.svg /usr/share/icons/elementary/places/48/distributor-logo.svg.original
sudo ln -s /usr/share/icons/Humanity/places/48/distributor-logo.svg /usr/share/icons/elementary/places/48/distributor-logo.svg

sudo mv /usr/share/icons/elementary/places/64/distributor-logo.svg /usr/share/icons/elementary/places/64/distributor-logo.svg.original
sudo ln -s /usr/share/icons/Humanity/places/64/distributor-logo.svg /usr/share/icons/elementary/places/64/distributor-logo.svg

sudo mv /usr/share/icons/elementary/places/128/distributor-logo.svg /usr/share/icons/elementary/places/128/distributor-logo.svg.original
sudo ln -s  /usr/share/icons/elementary/places/128/distributor-logo.svg

sudo mv /usr/share/icons/elementary-mono-dark/panel/22/start-here.svg /usr/share/icons/elementary-mono-dark/panel/22/start-here.svg.original
sudo ln -s /usr/share/icons/Humanity-Dark/places/22/start-here.svg /usr/share/icons/elementary-mono-dark/panel/22/start-here.svg
```

_TO UNDO (REVERT) THE ICON CHANGE_

Overwrite the links with the original "e" icons...

```
sudo mv /usr/share/icons/elementary/panel/22/start-here.svg.original /usr/share/icons/elementary/panel/22/start-here.svg

sudo mv /usr/share/icons/elementary/panel/24/start-here.svg.original /usr/share/icons/elementary/panel/24/start-here.svg

sudo mv /usr/share/icons/elementary/places/24/distributor-logo.svg.original /usr/share/icons/elementary/places/24/distributor-logo.svg

sudo mv /usr/share/icons/elementary/places/48/distributor-logo.svg.original /usr/share/icons/elementary/places/48/distributor-logo.svg

sudo mv /usr/share/icons/elementary/places/64/distributor-logo.svg.original /usr/share/icons/elementary/places/64/distributor-logo.svg

sudo mv /usr/share/icons/elementary/places/128/distributor-logo.svg.original /usr/share/icons/elementary/places/128/distributor-logo.svg

sudo mv /usr/share/icons/elementary-mono-dark/panel/22/start-here.svg.original /usr/share/icons/elementary-mono-dark/panel/22/start-here.svg
```

---

