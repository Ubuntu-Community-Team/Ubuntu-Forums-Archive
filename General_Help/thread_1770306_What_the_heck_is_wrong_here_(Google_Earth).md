---
title: "What the heck is wrong here? (Google Earth)"
date: 2011-05-29
forum: General Help
---

### Post by fpgdu on 2011-05-29
This is the crap I get when I try to use Google Earth (see attachment please).

 I've tried using safe graphics mode-- it doesn't work. When I installed it it says it was not a trusted package and now that it's installed, I cant find it in Synaptic Package Manager nor Ubuntu Software Center. I originally downloaded it as a deb from google.
 Could this be malware?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Uninstall it. 

Here is how you can install it from from the PPA (stable) repository:

[http://cinderbox.net/2011/05/11/how-to-install-google-earth-on-ubuntu-11-04-natty-narwhal-ppa/](http://cinderbox.net/2011/05/11/how-to-install-google-earth-on-ubuntu-11-04-natty-narwhal-ppa/)

Let me know if that works for you.

---

### Post by katykat on 2011-05-29
If its typical google garbage, its probably not even registered with the Apt/DPKG system and may not be in Synaptic. 

May need to search and destroy. 

Hunt for the deb and use a good file manager such as mc or gnome-commander to look inside it and figure out which files cam with it and where they installed. 

Then turn the BFG on it. 

Utter garbage, like google chrome. 

Its basically all spyware, and one would do well to blacklist the google trackers. 
Moblock (and dont forget to add the lists) would probably help.....

---

### Post by Ian Chesterton on 2011-05-29
Add Medibuntu and install GE from there.  Worked fine for me.  (On Lucid, anyway)

---

### Post by fpgdu on 2011-05-29
> **linuxinstalledfromhdd said:**
> Uninstall it. 

Here is how you can install it from from the PPA (stable) repository:

[http://cinderbox.net/2011/05/11/how-to-install-google-earth-on-ubuntu-11-04-natty-narwhal-ppa/](http://cinderbox.net/2011/05/11/how-to-install-google-earth-on-ubuntu-11-04-natty-narwhal-ppa/)

Let me know if that works for you.


Thanks for your reply :)

That's an article for INSTALLING it, not UNINSTALLING it.

---

### Post by fpgdu on 2011-05-29
> **katykat said:**
> If its typical google garbage, its probably not even registered with the Apt/DPKG system and may not be in Synaptic. 

May need to search and destroy. 

Hunt for the deb and use a good file manager such as mc or gnome-commander to look inside it and figure out which files cam with it and where they installed. 

Then turn the BFG on it. 

Utter garbage, like google chrome. 

Its basically all spyware, and one would do well to blacklist the google trackers. 
Moblock (and dont forget to add the lists) would probably help.....

Does it track activities outside of the program  itself?

---

### Post by fpgdu on 2011-05-29
> **Ian Chesterton said:**
> Add Medibuntu and install GE from there.  Worked fine for me.  (On Lucid, anyway)

I already had the Medibuntu repository long before installing Google Earth. However, Google Earth still wasn't listed anywhere.

---

### Post by fpgdu on 2011-05-31
bump

---

### Post by linuxinstalledfromhdd on 2011-05-31
Are you using the stable version from the PPA?

---

### Post by oldos2er on 2011-06-01
Install ttf-mscorefonts-installer, reboot.

---

### Post by linuxinstalledfromhdd on 2011-06-01
Whenever you freshly install Ubuntu there are plenty of extras you are gonig need to add to your system to run all the other software you are going to download eventually:

Check these helpful guides if you are new to Ubuntu

For 11.04
[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)



For 10.10
 [http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)



Goodluck..

---

