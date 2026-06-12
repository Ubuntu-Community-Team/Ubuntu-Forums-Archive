---
title: "How to enable USB in Virtualbox"
date: 2011-12-25
forum: General Help
---

### Post by waterbob on 2011-12-25
Hi, I use virtualbox on Ubuntu 11.10 as my host, I am trying to enable USB in my guest os (Windows 7), any help would be nice. :D

---

### Post by wildmanne39 on 2011-12-25
Hi, you need to install the guest additions and extension packs here is a link for that it has the package to download for extension pack and directions for all things virtualbox.
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
Thanks

---

### Post by westie457 on 2011-12-25
Further to wildmanne39's advice you have to use the version from the virtualbox website and the extension pack plus guest additions must match the version number.

Plus you must add yourself to the vboxusers group, unfortunately I cannot explain how to do this if you are running 11.04 or 11.10. In 10.10 you can do this by System > Administration > Users and Groups. Click on 'Manage Groups', scroll down the list to 'vboxusers' highlight and click on 'Properties'. In the pop up window check the box next to your name, click okay then enter your password and 'Authenticate'.

---

### Post by Bobhuber on 2011-12-25
To add yourself to the vbox users group in 11.10

[http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/](http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/)
[]("http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot/")

---

### Post by waterbob on 2011-12-25
> **Bobhuber said:**
> To add yourself to the vbox users group in 11.10

[http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/](http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/)
[]("http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot/")
Do you have a link to an easier tutorial?

---

### Post by dcstar on 2011-12-25
> **waterbob said:**
> Hi, I use virtualbox on Ubuntu 11.10 as my host, I am trying to enable USB in my guest os (Windows 7), any help would be nice. :D

What do the various posts in the Virtualization forum say?

---

### Post by wildmanne39 on 2011-12-25
Hi, the easiest thing to do is to read the documentation at the link I gave you so when you run into other problems you will be familiar with virtualbox.

On the download page is the link to download extension packs, you will be asked what application to install then choose virtualbox, then follow the directions on there site to install guest additions because there site is the most up to date.
Thanks

---

### Post by layers on 2011-12-26
I've installed VBox many times, and never had to do any account stuff to get USB working. All I remember, is that there are two versions of VBox - go get the one from here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) . Used it many times, with no errors. It even does printing when Wine cannot sometimes. An make sure you install guest additions.

---

### Post by Bobhuber on 2011-12-26
> **waterbob said:**
> Do you have a link to an easier tutorial?
Unfortunately no ( not unless something has changed)  with Oneiric and Unity. If you are using gnome3 it becomes much easier.
You can add gnome system tools which includes a users administration application.
The easiest way to get the most recent version of Vbox from Oracle's website is to add there repository 
[http://download.virtualbox.org/vertualbox/debian](http://download.virtualbox.org/vertualbox/debian) oneric. You may still have to get the extensions from the website the first time you install the progrm (can't remember). Why the developers made it so hard to add and change user rights and groups in 11.10 Oneiric Unity I have no idea. Absolutely ridiculous to have to use the terminal for such an important function. Hopefully this has or will change with the next release.

---

