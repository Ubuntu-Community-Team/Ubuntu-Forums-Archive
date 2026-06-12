---
title: "my research sais no how ever is possible"
date: 2011-04-11
forum: General Help
---

### Post by Adrienk on 2011-04-11
Every where I look you can install the gnome shell on ubuntu 10.10 but i want the gnome from the gnome site. I want the gnome 3 thats coming on fedora 15 to be running on ubuntu 10.10 the true and native gnome 3 not this shell replacement .....

is it possible?

---

### Post by bodhi.zazen on 2011-04-11
I have not tried it, but I do not think gnome3 is stable. 

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

> This package contains packages from GNOME3 and their dependencies so they [color=blue]can be used in Ubuntu 11.04[/color] (Natty). [color=darkred]**This PPA is EXPERIMENTAL and MAY BREAK YOUR SYSTEM. There is no downgrade process.[/color]**

I emphasized some sections. F15 is also in development.

Are you willing to tolerate a broken system ? file bug reports ?

---

### Post by Adrienk on 2011-04-11
That one doesnt work:

I am able to add it through sudo apt-add-repository ppa:gnome3-desktop/gnome3

then I go sudo apt-get update

It states that those repositories added throw 404 (its a warning) which are ubuntu-desktop/gnome3-builds from launchpad.

So i ignore then do a regular update and there are no files to upgrade. so I do a dist-upgrade.
I get: 0 new files. Since I added this to the software sources should there not be updates?

Trying the apt-get install gnome-desktop3 throws a unable to locate package gnome-desktop 3.

Trying to add the

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main  deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) natty main 

to the sources.list file throws errors on the dist-upgrade 
stating that it cant find specific links to packages. It then throws the same
issues on trying to install the gnome-desktop3

also gnome 3 the live cd is stable it was released just recently to the general public and fedora 15 is implementing it. I was hoping to upgrade in such away that when i go to "about gnome" it sais gnome 3.0

I also tried through the software center and it stated that I need to check my internet connection - which I dont or i wouldnt be posting on this forum,
 that the packages and updates it wanted couldnt be reached because of 404 errors

---

