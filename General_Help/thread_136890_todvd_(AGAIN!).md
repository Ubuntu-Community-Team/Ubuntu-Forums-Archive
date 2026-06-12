---
title: "todvd (AGAIN!)"
date: 2006-02-26
forum: General Help
---

### Post by neoroses on 2006-02-26
hiya im simply trying to install tovid, i have tried with the .deb and apt-get and i just get this back:

sam@tuxxx:~$ sudo apt-get install tovid
Reading package lists... Done
Building dependency tree... Done
tovid is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  tovid: Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
sam@tuxxx:~$

i have python installed and jpegtool or what ever it is lol (i think) and i have the spt sources list from the sticky post in the sources list forum....so could some one pleeeeeeeeeeeeeeeeeeeease help me asap??


neoroses

---

### Post by pestilence4hr on 2006-02-26
> tovid: Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed

Well, that seems to be a problem ;)

Maybe you could try installing from source?  Assuming you have the apt-src for tovid in your /etc/apt/sources.list, do

```
apt-get build-dep tovid
apt-get -b source tovid
dpkg -i tovid*.deb

```

---

### Post by neoroses on 2006-02-26
well i thought i did but when i run apt-src for tovid i get - 
sam@tuxxx:~$ sudo apt-get build-dep tovid
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for tovid

do you no or no where i kan get it the apt-src from adress from??

thanks for your help m8 :D

---

### Post by pestilence4hr on 2006-02-26
Don't know.  Just get the source from the official website:  [http://prdownload.berlios.de/tovid/tovid-0.25.tar.gz](http://prdownload.berlios.de/tovid/tovid-0.25.tar.gz)

then:

```

sudo apt-get build-dep tovid
tar zxvf tovid-0.25.tar.gz
cd tovid*
./configure
make
sudo make install

```

Report back.

---

### Post by neoroses on 2006-02-26
meep i appear to have some how messed up the entire apt-get system :S im getting errors left rite and centre im guna start afresh lol i have done a lot of messing today as im linux curious n i think now i av messed to far lol

thanks a lot for your help :D

neoroses

---

### Post by pestilence4hr on 2006-02-26
[QUOTE=neoroses]meep i appear to have some how messed up the entire apt-get system :S im getting errors left rite and centre im guna start afresh lol i have done a lot of messing today as im linux curious n i think now i av messed to far lol

thanks a lot for your help :D

neoroses[/QUOTE]

Most errors are fixable, with probably less effort and more satisfaction than reinstalling.  But suit yourself :-D

---

### Post by siucdude on 2006-03-05
forget tovid its goodb but there is something new and i would recomand.  DeVeDe should be same repo.  try it out.

thanks

---

### Post by jtpratt on 2006-03-16
DeVeDe doesn't work at all for me.  It installed fine and crashes whenever I try to load a video.  Their site is all in Spanish except for the download page, I couldn't get any help.

your python dependancy problem can be solved by running these two commands:
$ sudo apt-get install python-wxgtk2.4
$ sudo apt-get install python-dev

find that and other tips for converting video in 5.10 Ubuntu on my help page:
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

---

