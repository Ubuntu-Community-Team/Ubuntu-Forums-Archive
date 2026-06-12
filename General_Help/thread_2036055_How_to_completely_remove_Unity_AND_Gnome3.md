---
title: "How to completely remove Unity AND Gnome3?"
date: 2012-08-01
forum: General Help
---

### Post by 4your411 on 2012-08-01
Just like the OP says, what is the best way to remove both Unity and Gnome3?

Some of you might ask why I don't do 1 of two things....

1. Just pile on more desktop environments.

2. Do a fresh install of Xubuntu, or whatever.

I do not want to pile on lots of desktop environments because I am trying to make backups with Remastersys. I need space for all the apps I am adding.

I do not want to do a fresh install because I have a distro that no longer exists that is all the way back from Lucid, and I have done a lot of tinkering to get a really awesome collection of applications, some of which would be hard to find again. I want to upgrade, but I do not like Unity or Gnome3. I want something more like a traditional desktop with a start menu, and I do not use touch screens. 


So now that we have that out of the way, how can I get rid of the Gnome3 AND Unity environments and add something else?

I ultimately prefer XFCE, just because I really like it on modern hardware with no lag. If there are any complications due to XFCE and Gnome sharing libraries (More in GTK2 than GTK3, right?), then I could potentially go with KDE or LXDE temporarily, or something even lighter like WindowMaker or Awesome or E17.

Also, I do not necessarily want to "purge" everything that is Gnome related, especially GTK2. I dont care about having a 'pure' XFCE session. I like certain Gnome and even KDE tools. I do not want my wifi to suddenly stop working. I just want the actual desktop sessions to vanish along with stuff that will not be relevant on XFCE.


I could use instructions for 11.04 as well as for 12.04.

Thank you for your help.

---

### Post by idoitprone on 2012-08-01
```
sudo apt-get install xubuntu-desktop
sudo apt-get purge ubuntu-desktop
sudo apt-get purge gnome-desktop

```
it should only remove packages that are not needed by xubuntu-desktop

if it is missing the package, then just reinstall it.

there shouldnt be any problem with gnome and xfce using the same libraries, because the libraries are designed to modular and to be shared

---

### Post by mastablasta on 2012-08-01
to get only Xubuntu and XFCE you do it like this: [http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)
 
solutions for other desktops are also provided.

---

### Post by xachu4u on 2012-08-01
i thought it was impossible...if it is successful, then please post it here.

---

