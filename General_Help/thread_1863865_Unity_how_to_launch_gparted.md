---
title: "Unity: how to launch gparted?"
date: 2011-10-18
forum: General Help
---

### Post by fgrieu on 2011-10-18
I used to boot ubuntu-10.10-desktop [*], pull the System/Administration/Gparted menu, and live happy.

Now I'm trying that with ubuntu-11.10-desktop, and can't figure it out. Or launch a terminal, from which I could do something.

I'm open to anything: a 1 minute crash course on Unity, a recipe to remove Unity from a boot CD or USB stick..

TIA!

[*] often from a USB stick with persistent storage made with Universal-USB-Installer

---

### Post by mikejonesey on 2011-10-18
not installed by default even though it's installed on the live cd... sudo apt-get install gparted... ps you wont be able to modify mounted partitions... (with gparted anyways...)

(i'm not a unity user so can't advice on terminal other than try Alt+F2 and type gnome-terminal... doh maybe not... it's not gnome... hmm u'll have to wait for a unity user for that, try a search in the menu...)

ps you have tried Ctrl+Alt+t ?

---

### Post by thatguruguy on 2011-10-18
The live disk has gparted on it, since it is essential for the installation.  It isn't installed by default when you actually install Ubuntu to your desktop.

There is some limited functionality in the "Disk Utility" which you can get to by opening the dash and typing "disk" (without the quotes, of course).

Or, if you need to full power of gparted, you can install it from the Ubuntu Software Center (it's a featured app, at least on mine), or by typing the following in a terminal:

```
sudo apt-get install gparted
```

---

### Post by fgrieu on 2011-10-18
Thanks all.

Opening the dash and typing: yes that works (I need to type "gpqrted" until I manage to select the FR keyboard under Unity).

Further Gparted **IS** in that "dash" thing, under "More apps"; the top 2/5 of the name "GParted Partition Editor" are even visible.

Ctrl+Alt+t: yes it opens a terminal!

---

