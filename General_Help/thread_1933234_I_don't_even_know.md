---
title: "I don't even know"
date: 2012-02-28
forum: General Help
---

### Post by tinkerist on 2012-02-28
What the he'll do I do I with this?

---

### Post by rollinsmoke on 2012-02-28
what is that your display

or i should say is that all you see on your display

---

### Post by tinkerist on 2012-02-28
Yep, that's it. This happened when I tried to upgrade from 11.04 to 11.10.

---

### Post by rollinsmoke on 2012-02-28
hmm.. whats your video card and can you log into your terminal to do so you just click on the the gear on your login screen and change it to i cant remeber what it is ill look 


if you can write this down and type in 


[COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

[COLOR=Black]for nivida and 
[/COLOR][/COLOR][COLOR=Red]
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper  debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases[/COLOR]

[COLOR=Red]cd

mkdir catalyst && cd catalyst[/COLOR] [COLOR=Red]

wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run)[/COLOR] [COLOR=Red]

sh ./ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/oneiric[/COLOR] [COLOR=Red]

sudo dpkg -i fglrx*.deb[/COLOR] [COLOR=Red]

sudo aticonfig --initial -f[/COLOR] 


for ati (i think) i found these on google but from the looks of things your video drivers arn't working well with the upgrade but i am a noob myself so its all kinda a shot in the dark for me but thats what i would try 


Its called recovery console btw




also when you say you tried did you succeed in updating as in did it go through the whole process then you got this screen or did you lose power Internet ect... during the upgrade

---

### Post by tinkerist on 2012-03-01
after a few restarts, it seemed to solve itself.  although it still shows the same screen while in startup.

---

### Post by rollinsmoke on 2012-03-01
are you sure your using the most current video drivers for your version of ubuntu i had to update mine as well atleast for the official ones

---

