---
title: "Remove X"
date: 2006-05-03
forum: General Help
---

### Post by flebber on 2006-05-03
Hi 

I had a problem with X I posted here that no one could solve so I reckon my next option is to totally remove X and reinstall it to see if fresh install resolves my issue.

However i go to use apt to remove X and it cannot find package to remove.

I have tried

apt-get remove X
apt-get remove Xorg
apt-get remove xorg
apt-get remove x-server

but I cannot find the right name for X to remove it, any ideas ?

---

### Post by Rog131 on 2006-05-03
Ubuntu packages ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) is your friend.

Search the contents of packages with keyword xorg ->

Package: xserver-xorg
Package: xorg-driver-fglrx (if you have Ati-fglrx)
Package: xserver-xorg-driver-i810 (if you have Intel i8xx, i9xx display driver)

and so on...

---

### Post by flebber on 2006-05-03
Thanks for that, will run it up the flagpole and see if it salutes.

---

### Post by ComplexNumber on 2006-05-03
[quote=flebber]Hi 

I had a problem with X I posted here that no one could solve so I reckon my next option is to totally remove X and reinstall it to see if fresh install resolves my issue.

However i go to use apt to remove X and it cannot find package to remove.

I have tried

apt-get remove X
apt-get remove Xorg
apt-get remove xorg
apt-get remove x-server

but I cannot find the right name for X to remove it, any ideas ?[/quote] **do not** remove the X packages whilst you are still using them (ie when you are using kde or a windows manager). from the login manager, go into 'sessions' and choose to boot into the terminal (if you have xterm installed). uninstall X server from there.

---

### Post by flebber on 2006-05-03
I am at the console, that is the problem I am having all window managers are dead, X not working at all

---

### Post by flebber on 2006-05-04
I reinstalled X but it still is not working this error still remians > FreeFontPath FPE "/usr/share/X11/fonts/misc" refcount is 2 should be 1 fixing. After this error X quits and cannot be started. Any Ideas ?

---

### Post by barbarian on 2006-05-04
1. ctrl-alt-F1
2. sudo aptiude update
3. sudo aptitude remove x-window-system-core

---

