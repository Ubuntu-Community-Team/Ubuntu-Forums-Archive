---
title: "Ubuntu Won't AutoMount anything"
date: 2009-12-30
forum: General Help
---

### Post by madprofessor on 2009-12-30
Recently I added a program that required me to install a few things. One slip up and I accidentally uninstalled network-manager. I was able to successfully get it back fully but the issue now is Ubuntu will not automount anything, cds, dvds USB drives, nothing. What could have happened that caused this and what is a possible solution?

---

### Post by dcstar on 2009-12-31
> **madprofessor said:**
> Recently I added a program that required me to install a few things. One slip up and I accidentally uninstalled network-manager. I was able to successfully get it back fully but the issue now is Ubuntu will not automount anything, cds, dvds USB drives, nothing. What could have happened that caused this and what is a possible solution?

Applications-System Tools-Configuration Editor

Set the **/desktop/gnome/volume_manager/automount_media** & **/desktop/gnome/volume_manager/automount_drives** keys.

---

### Post by madprofessor on 2009-12-31
Those keys don't exist. Should I add them?

---

### Post by dcstar on 2009-12-31
> **madprofessor said:**
> Those keys don't exist. Should I add them?

Firstly add a new user to your system and log into it, if the automounts suddenly work then have a look at those settings for the new user and see if you can replicate them in the original user account.

Those keys may not be on a 9.10 system, try the mount options in Nautilus.

---

### Post by madprofessor on 2009-12-31
I created a new user and logged in and no automount. I don't know what got broken but not only this, plus i can't install any themes (I've already tried to reinstall "human" to no avail). plus under Connect To Server I only have "Custom Server". I am clueless as to what happened.

---

### Post by dcstar on 2010-01-01
> **madprofessor said:**
> I created a new user and logged in and no automount. I don't know what got broken but not only this, plus i can't install any themes (I've already tried to reinstall "human" to no avail). plus under Connect To Server I only have "Custom Server". I am clueless as to what happened.

You may want to look as the "program" you installed that has obviously broken a lot of things.

---

### Post by madprofessor on 2010-01-01
The program by the way is called EtherApe. It's a graphical network map. Basically it shows the different nodes on your network and the protocols that each uses to connect. I installed this on my netbook using a different method and it worked fine. I installed the dependencies it stated it needed when I ran ./configure instead of installing the dependencies the website said it needed.  Apparently one of these programs is what messed up my OS.

---

