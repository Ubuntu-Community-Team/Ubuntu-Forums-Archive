---
title: "Gnome 3.0 --&gt; Gnome 3.0.1"
date: 2011-04-30
forum: General Help
---

### Post by scott-ian on 2011-04-30
I installed Gnome 3 on Natty, and have found that Gnome 3.0.1 has been released, but I am using Gnome 3.0.0.  How can I upgrade?  Is it stable yet?

---

### Post by lithopsian on 2011-04-30
Where did you install it from?  It isn't in the Ubuntu repos.

There is a PPA and I imagien it will be there soon.  Otherwise you'll have to build it yourself.

---

### Post by scott-ian on 2011-05-01
I followed the instructions here: [http://blog.sudobits.com/2011/04/26/how-to-install-gnome-3-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/26/how-to-install-gnome-3-on-ubuntu-11-04/)

---

### Post by Deadboy420 on 2011-05-03
For Gnome 3.0.1 add this ppa:
```
sudo add-apt-repository ppa:ricotz/testing 
```then use Update Manager as you normally would to upgrade packages.

*Btw,** System Settings > System Info** still shows 3.0.0 for me but the installed package is at 3.0.1

---

### Post by scott-ian on 2011-05-03
> **Deadboy420 said:**
> For Gnome 3.0.1 add this ppa:
```
sudo add-apt-repository ppa:ricotz/testing 
```then use Update Manager as you normally would to upgrade packages.

*Btw,** System Settings > System Info** still shows 3.0.0 for me but the installed package is at 3.0.1
How stable is that?

---

### Post by andrewthomas on 2011-05-03
If you are looking for up-to-date and the least-intrusive to your system, then I would suggest building in your /home directory using the jhbuild tool.
 
There are instructions in the first post of this thread.
 
[http://ubuntuforums.org/showthread.php?t=1603874&highlight=jhbuild](http://ubuntuforums.org/showthread.php?t=1603874&highlight=jhbuild)

---

### Post by qamelian on 2011-05-03
> **andrewthomas said:**
> If you are looking for up-to-date and the least-intrusive to your system, then I would suggest building in your /home directory using the jhbuild tool.
 
There are instructions in the first post of this thread.
 
Gnome
Those instructions are only for Gnome-shell, not the entire Gnome 3 environment.

---

### Post by andrewthomas on 2011-05-03
> **qamelian said:**
> Those instructions are only for Gnome-shell, not the entire Gnome 3 environment.
But all you have to do is change the module-set and you can build all of GNOME with jhbuild.
 
For further reference:
 
[http://live.gnome.org/JhbuildOnUbuntu](http://live.gnome.org/JhbuildOnUbuntu)
 
[http://live.gnome.org/Jhbuild](http://live.gnome.org/Jhbuild)

---

### Post by scott-ian on 2011-05-03
> **andrewthomas said:**
> But all you have to do is change the module-set and you can build all of GNOME with jhbuild.
 
For further reference:
 
[http://live.gnome.org/JhbuildOnUbuntu](http://live.gnome.org/JhbuildOnUbuntu)
 
[http://live.gnome.org/Jhbuild](http://live.gnome.org/Jhbuild)
Where can I get the source code?

---

### Post by andrewthomas on 2011-05-03
> **scott-ian said:**
> Where can I get the source code?

Read the gnome.org links.  You just use git to keep in sync with the latest code.

---

