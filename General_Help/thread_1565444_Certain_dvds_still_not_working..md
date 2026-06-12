---
title: "Certain dvds still not working."
date: 2010-08-31
forum: General Help
---

### Post by jameshampshire on 2010-08-31
alright well in the past week since ive installed linux ive installed every plugin codec known to man. i had a problem with my skins dvd to i cant remember what i found to get that working. now my avenged sevenfold dvd isnt working saying it needs plugins.
someone please help me out.

don't direct me to the same old terminal command to install totems plugins.
ive already installed them this dvd isnt working. and for some reason on ubuntu when i try to update things say movie player to find the codecs by itself i get an error message.

---

### Post by PRC09 on 2010-08-31
Along with the codecs you also need the following......


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jameshampshire on 2010-08-31
james@james-desktop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apport-hooks-medibuntu is already the newest version.
The following NEW packages will be installed:
  app-install-data-medibuntu
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 14.5kB of archives.
After this operation, 102kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  app-install-data-medibuntu
E: There are problems and -y was used without --force-yes



i got that and my dvd is still not playing.
it played before but i had ugly lines through the video.
closed movie player reopened it and its not working again.

---

### Post by jameshampshire on 2010-08-31
i dont worry hang on i think i may of found what you meant.

---

### Post by jameshampshire on 2010-08-31
nope sorry it didnt work.


ahhh frustration!

---

### Post by XAZero on 2010-09-01
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
sudo apt-get install ffmpeg libavcodec-extra-52


sudo /usr/share/doc/libdvdread4/install-css.sh

the first (long) command is the way i add the medibuntu repo and also installs some codecs i think you might be missing 

the second one is the one that enables encripted dvd playback
(assuming you have installed the restricted extras)

---

### Post by jmore9 on 2010-09-01
Did you go here and follow the steps  here ?

Comprehensive Multimedia & Video Howto

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Has a lot of stuff to install.  And some troubleshooting also.

---

### Post by jameshampshire on 2010-09-01
hey guys it still won't work i get this

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Something wicked happened resolving 'archive.ubuntustudio.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_AU.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_AU.bz2)  Something wicked happened resolving 'archive.ubuntustudio.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.ubuntustudio.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


i had a problem with my skins dvd (skins-tvshow) last week
i don't know how but i fixed it and it managed to play the dvd.
this was before my os crashed and i had to reinstall linux.
same crap happened with the same dvd and i tried my best to do whatever i did to get it working.
it pays the dvd but only the warning messages and such at the start. wont jump to the menu nor play the movie. if i click the menu option it won't go to the menu and just restarts with the warning messages.
i have no problem with this in vlc. but i don't wanna just ditch movie player i'd like it working.
ive been to the mediabuntu linux site tried to install it.
i just get that ^ same error everytime. its doing my head in please help me.

---

