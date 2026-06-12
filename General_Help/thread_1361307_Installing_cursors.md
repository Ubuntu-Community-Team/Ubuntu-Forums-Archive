---
title: "Installing cursors"
date: 2009-12-21
forum: General Help
---

### Post by linux_dream on 2009-12-21
Hi,
I'm trying to install new cursors.  I've downloaded Crystalcursors.  I extracted it into my desktop.  I typed in a terminal : 
cd Desktop
cd Crystalcursors
make
make install
If I remember well.  Now I go to the list of cursors, I see more cursors than I had, but I can't change of cursors.  Whenever I push on "install", it doesn't do anything.  
I guess there was an error during the installation?  What can I do?

---

### Post by MelDJ on 2009-12-21
try dragging and dropping the package .tar.gz or zip package file into the appearances window

---

### Post by Isengrin on 2009-12-21
> **linux_dream said:**
> Hi,
I'm trying to install new cursors.  I've downloaded Crystalcursors.  I extracted it into my desktop.  I typed in a terminal : 
cd Desktop
cd Crystalcursors
make
make install

Compiling cursors? xD

If you use GNOME, just go to Appearance in the Setting menu, and select 'install themes' or something like that. :3

My favourite way is extracting the package in /usr/share/icons and adding
```
Xcursor.theme:Theme_Name
```
to ~/.Xdefaults

> **linux_dream said:**
> I guess there was an error during the installation?  What can I do?
Some people doesnt' package GTK and cursor themes properly, or the correctly packaged theme is inside another package. Look if there is a package inside the one you downloaded.

---

### Post by steveneddy on 2009-12-21
> **MelDJ said:**
> try dragging and dropping the package .tar.gz or zip package file into the appearances window

That is the easiest way.

---

### Post by linux_dream on 2009-12-22
> **MelDJ said:**
> try dragging and dropping the package .tar.gz or zip package file into the appearances window
I tried to drop the .tar into the Appearances window but it said it doesn't seem to be a valid theme.
It's not a theme, it's a collection of cursors.  Here's where I downloaded it: [http://gnome-look.org/content/show.php/crystal+xcursors?content=6240](http://gnome-look.org/content/show.php/crystal+xcursors?content=6240).
It is the second most downloaded cursors of the website.  I don't think there's a problem with the files... 
I also tried install themes from the Appearances window, but I got exactly the same problem.
Any other idea?
Thanks for the help until now!

---

### Post by Isengrin on 2009-12-22
Ok... I downloaded it and, to be honest, I have not idea how does it work, altough the makefile now makes sense to me. xD

---

### Post by linux_dream on 2009-12-22
> **Isengrin said:**
> Ok... I downloaded it and, to be honest, I have not idea how does it work, altough the makefile now makes sense to me. xD
Hmm ok.  I guess I just have to wait for someone else to enlighten us then.  Thank you anyway for your help.

---

