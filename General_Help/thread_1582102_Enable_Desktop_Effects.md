---
title: "Enable Desktop Effects"
date: 2010-09-26
forum: General Help
---

### Post by techunit on 2010-09-26
Hey guys, I am trying to do some video tutorials at [http://ubuntuvideotutorials.org](http://ubuntuvideotutorials.org) on Ubuntu Netbook Edition 10.10 this is the first edition to require desktop effects. When I install it in the VM it isn't enabled right away. when I go to enable it I ran in to the problem that I couldn't find appearance. When I opened appearance from the terminal I couldn't enable Visual effects because mutter is running. How do I drop to the base terminal and enable visual effects?

---

### Post by kerry_s on 2010-09-26
you can not because mutter is the compositor & the desktop. log out & select "gnome" if you want to use compiz.

---

### Post by techunit on 2010-09-26
That seems strange because Unity appears to need effects. I am not talking about the old Lucid UNE I am talking about Unity... Right now all the effects are slowed to a crawl...

---

### Post by vegetarianshrimp on 2010-09-26
The new Unity interface uses mutter as it's windows manager. (something somewhere in between metacity and compiz, IMO) Right now, you can't replace that with compiz and still get the unity interface. You would have to install ubuntu-desktop and select Gnome on the login screen to use compiz, but you wouldn't get the Unity interface, just a plain desktop.

---

### Post by techunit on 2010-09-26
I am not stupid. I understood that the first time.  I am wondering if there is supposed to be some kind of visual effects of acceleration that runs the Unity interface. right now it runs a crawl taking about 40 seconds to load the menu. and titles for the docklets take 20seconds to appear. It is terribly slow on the vm configured with 2GB of ram, 4 2.66GHz cores. It shouldn't be that slow.

---

### Post by hrickh on 2010-09-26
> **techunit said:**
> It shouldn't be that slow.
It shouldn't be, but it is.

Search outside of ubuntuforums.com and you'll quickly realize that it's a common problem that currently has no "fix".

R.
==

---

### Post by kerry_s on 2010-09-26
it's probably because your running in a vm.

i am running unity, so i do know what your talking about.

---

