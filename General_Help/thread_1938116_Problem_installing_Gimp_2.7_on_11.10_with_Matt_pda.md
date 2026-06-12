---
title: "Problem installing Gimp 2.7 on 11.10 with Matt pda"
date: 2012-03-09
forum: General Help
---

### Post by victorgb on 2012-03-09
Hello all 

I just installed 11.10 and getting used to it :-)
I am having problems installing Gimp 2.7 with this method.

sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update
sudo apt-get install gimp

I get this error !! Is there a nother way I can use Please help ?

"victor@victor-Xtreme:~$ sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
[sudo] password for victor: 
You are about to add the following PPA to your system:
 PPA named mrw-gimp-svn for matthaeus123
 This is a repository for all of the Gimp trunk git builds that I want.
I guess this would be considered a nightly build PPA, but these builds are not build every night automatically rather built whenever I get around to it, which might be several builds per day or one build per week.


If you have any critical runtime errors that might be  caused by build config problems or have any ideas for patches, feel free to email me.


These packages do not include any patches were they built with any special configurations


GPG Key:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB

GIMP 2.7.5 Will not work with the current glib and gtk in Oneiric. To fix the problem install these repos

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main 

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main 
 More info: [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)
Press [ENTER] to continue or ctrl-c to cancel adding it"

I have tried this several times with no luck. 
Please note I have installed these 2 repo's as well and dis updates.

"deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) oneiric main 

deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) oneiric main "

and still no luck. My systems ask me to do a partial upgrade where it uninstalls Gimp 2.6 and still does not install Gimp 2.7.5 wih dependency errors.

Kind regards
Victor
South Africa.

---

