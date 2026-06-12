---
title: "Gnome 3"
date: 2011-09-14
forum: General Help
---

### Post by suryaD on 2011-09-14
hey guys.its me once again..i have this strange doubt umm the thing is if i install GNOME 3 on my ubuntu 11.04 will it erase all my existing files and softwares on my current ubuntu 11.04...? if no then gnome 3 is awesome..it has good GUI..

---

### Post by nitstorm on 2011-09-14
Installing Gnome3 will not delete your existing softwares and files, but it will remove some of your packages. And if you decide to come back to Unity, you will need to reinstall those deleted packages again. Also, fair caution - there are a quite a few applications that are not compatible with Gnome3. For more instructions on how to install/remove Gnome3 refer to [this guide on askubuntu.com]("http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3")

---

### Post by suryaD on 2011-09-14
thnku for the informative article

---

### Post by garvinrick4 on 2011-09-14
Every one has a bit of different way to set up there machine. I took a fresh install of
Natty 11.04 and installed the gnome-shell ppa for Natty as per below and put it in a 10 gig partition of its own and it runs smooth as silk. You can of course run one install and change at login screen if preferred way. I just leave mine in gnome-shell (gnome3 is actually called gnome-shell when added as package, also referred to as gnome-shell). This is just a personal preference, really runs nice though with all intel vanilla cards and drivers I have to add. Have not tried at all with the higher end graphics cards and such.
```
sudo add-apt-repository ppa:gnome3-team/gnome3
``` ```
sudo apt-get update
``````
 sudo apt-get install gnome-shell
```Here is link for ppa's, easy to install. As you see above.
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
Hope this helps in anyway. Enjoy your Ubuntu

---

### Post by Quackers on 2011-09-14
I have unity running in 11.04 and gnome-shell works just fine. Both are interchangeable at the login prompt without any problems at all.

---

### Post by garvinrick4 on 2011-09-14
> **Quackers said:**
> I have unity running in 11.04 and gnome-shell works just fine. Both are interchangeable at the login prompt without any problems at all.
11.04 is just about as stable as it gets isn't it, is a joy to use.

---

### Post by Quackers on 2011-09-14
It is indeed. Fault-free as far as I can remember :-)

---

