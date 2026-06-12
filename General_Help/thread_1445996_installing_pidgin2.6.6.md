---
title: "installing pidgin2.6.6"
date: 2010-04-03
forum: General Help
---

### Post by nischalinn on 2010-04-03
I have pidgin2.5.2. I want to install pidgin2.6.6.How can I do that?
I've tried:
[B]xxx@xxxdesktop:~$ sudo apt-get install pidgin2.6.6
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/B]
I've also tried:

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8**
 [B]echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list[/B]
  
It doesnot work too.

**How can I install pidgin2.6.6?**

---

### Post by vzomik on 2010-04-03
you should use the command "sudo killall apt", or restart the computer, because the apt is running in background.

---

