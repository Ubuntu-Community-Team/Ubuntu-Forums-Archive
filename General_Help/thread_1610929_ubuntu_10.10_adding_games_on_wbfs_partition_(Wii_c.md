---
title: "ubuntu 10.10 adding games on wbfs partition (Wii console)"
date: 2010-11-01
forum: General Help
---

### Post by RastaManPower on 2010-11-01
hello guys i have a hacked wii and i want to put games in it. when i had windows installed i used wbfs manager but now on ubuntu i dont know how to do. what programs do i have to use to put games into my wbfs partition?

---

### Post by janpol on 2010-11-01
There is a tool called **Wiithon **that does that (I've never tried it tho, so I don't know of its capabilites).

---

### Post by RastaManPower on 2010-11-01
i tryed downloading the deb pcakage and installing it with software center but i get an error
Wrong architecture 'lpia'

---

### Post by drewsus on 2010-11-25
> **RastaManPower said:**
> i tryed downloading the deb pcakage and installing it with software center but i get an error
Wrong architecture 'lpia'

Download the i368 version

---

### Post by drewsus on 2010-11-25
You can add it via PPA with these commands: 

```
sudo add-apt-repository "deb http://ppa.launchpad.net/wii.sceners.linux/wiithon/ubuntu karmic main"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F882273
sudo apt-get update
sudo apt-get install wiithon
sudo gpasswd -a $USER disk
```

Then restart your session.

---

### Post by RastaManPower on 2010-11-25
thanks very much! install worked perfectly but i get an error when program loads. might be able to find some info on the net to fix this
Warning: 

You can not access the partition because the user who opened Wiithon does not belong to the group "disk", displaying games from the previous session

---

### Post by biodiesel-bri on 2010-11-27
Thanks, this worked perfectly for me.  I can now transfer games from one wbfs USB drive to another.

Rasta, did you do the last step?

```
sudo gpasswd -a $USER disk
```

After that you have to log out of your Gnome or KDE session and then log back in so the permissions take effect.

---

