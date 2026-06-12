---
title: "Pidgin and 9.10"
date: 2009-11-06
forum: General Help
---

### Post by StOoZ on 2009-11-06
Is there a way to install the latest pidgin on 9.10?

---

### Post by squaregoldfish on 2009-11-06
You should be able to add Pidgin's own repositories to get the latest version. See the [Pidgin installation guide]("http://www.pidgin.im/download/ubuntu/").

Steve.

---

### Post by scouser73 on 2009-11-06
Here's the PPA of Pidgin [[COLOR="Red"]**Launchpad PPA Pidgin**[/COLOR]]("https://launchpad.net/~pidgin-nateon/+archive/ppa")

---

### Post by coqui1212 on 2009-11-06
copy and paste the commands below in the terminal 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list


``` 
 
once copied hit update manager and download the newly available pidgin packages which get updated more often than the one included with ubuntu.

---

### Post by StOoZ on 2009-11-07
thanks a lot people!!

---

