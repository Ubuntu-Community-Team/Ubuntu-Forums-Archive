---
title: "Transmission update"
date: 2009-10-03
forum: General Help
---

### Post by shaon3343 on 2009-10-03
[SIZE=4][COLOR=Red]Can anyone give me the command to update the "Transmission" ? A command like : sudo apt-get install ... ?
 please help.
               shaon[/COLOR][/SIZE]

---

### Post by bumanie on 2009-10-03
Transmission updates will come through automatically when there are updates released. This goes for all 'official' software supported by Canonical which is installed on your system.

---

### Post by shaon3343 on 2009-10-03
[B][COLOR=Red]But my transmission version is 1.51. 
I know that the latest version is 1.72. So how can i update??[/COLOR][/B]

---

### Post by Vaphell on 2009-10-03
download and install manually
official repos are frozen before the release of a new Ubuntu version
it means that software versions are locked for stability reasons and only bug/security fixes are allowed for a given software included in current flavor of Ubuntu for stability reasons
Transmission was locked at 1.5 and in since then developers went to 1.7
You need to download .deb package or sources to compile and install yourself or find PPA with current version (PPA = additional entry on the list of app sources, will autoupdate)

edit:
[http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

btw you may want to try deluge, i find it much better

---

### Post by shaon3343 on 2009-10-03
**[COLOR=Red]Is it required to completely remove the current version of Transmission (1.51) before I install those .deb packages ( Version 1.75) ? please inform me. [/COLOR]**

---

### Post by Vaphell on 2009-10-03
i updated older software with deb files manually and it worked just fine
just double click it, check if app works afterwards

and for the love of god, stop using red font ;) it doesn't make it any more readable

---

### Post by geirha on 2009-10-04
I use the stable transmission PPA from here (There's a link to it from transmission's official website): [http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

Once the PPA (personal package archive) is added, you'll be able to update to 1.75 using the update manager.

In short, pasting the following into a terminal (and providing your password when sudo requires it) should make the newer versions available in the update manager.
```

sudo tee /etc/apt/sources.list.d/transmission.list << EOF
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main
EOF
gpg --keyserver keyserver.ubuntu.com --recv 976b5901365c5ca1
gpg --export --armor 976b5901365c5ca1 | sudo apt-key add -
sudo aptitude update

```

---

### Post by shaon3343 on 2009-10-05
**[COLOR=Purple]Thanks a lot to everyone, specially "geirha" after applying geirha's command I'm now upgraded to version 1.75 !!! THAAANNNNKSSS A LOT BUDDY!!! :-)[/COLOR]**

---

### Post by -jay- on 2009-11-09
thanks for the ppa links now upgraded to 1.76

---

