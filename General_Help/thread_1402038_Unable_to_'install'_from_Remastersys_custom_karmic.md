---
title: "Unable to 'install' from Remastersys custom karmic Dvd"
date: 2010-02-08
forum: General Help
---

### Post by inameiname on 2010-02-08
As of a few days ago, I am unable to install from a Remastersys Custom DVD to a blank drive.

I've updated my system and remade a  custom DVD/ISO a few separate times in the past few days, and each time  I type 'install', it merely loads to the point where it almost pops up  with the required thing, the language desired page I believe, but  doesn't and just goes straight to the 'live cd', or running off of the  DVD. 

I've also tried installing the release onto the hard drive  through the 'live cd' session, but it just pops up "the program ubiquity  has crashed". 

Being pretty skilled with Ubuntu and Linux in  general, I suspect one of the newest updates to my Ubuntu Karmic system  has conflicted with the Remastersys DVD/ISO production and restoration  in some way. I've backed up my Ubuntu through Remastersys, using the  'Backup Mode' dozens upon dozens of time, and this is the first time  this issue has come up.

So if anybody has found a solution to  this, that would be wonderful, especially as currently I'm unable to  restore my backup to my computer, or to the other couple computers I put  the clone of mine on.

---

### Post by inameiname on 2010-02-10
I tried the Ubiquity regression that Ive heard about, which is basically uninstalling the newest version of Ubiquity and putting on the original version from the Karmic repositories, but it doesn't seem to work either. Thus, it leads me to believe it's not necessarily Ubiquity as the main problem because I tried the original Karmic version, 2.0.6, and it still doesn't work or even open at all.

Is there any other way to install to the hard drive from a Remastersys Live Cd, without using Ubiquity, the traditional Ubuntu Installer?

---

### Post by Takoonrider on 2010-02-15
I have the same problem (ubuntu karmic) and found out that the ubiquity front-end was not installed. Try to look if you have the same problem:
apt-show-versions ubiquity-frontend-gtk

you might have to install the apt-show-versions package
sudo apt-get install apt-show-versions
apt-show-versions ubiquity-frontend-gtk

if it's not there try to install it
sudo apt-get install ubiquity-frontend-gtk

sudo ubiquity should now work so it's just to make a new live cd with remastersys

Hope it was helpfull

---

### Post by inameiname on 2010-02-15
Thanks for the suggestion, but unfortunately it did not fix the problem. 'Sudo ubiquity' still did not open anything. 

Ubiquity-frontend-gtk was already installed, along with ubiquity, ubiquity-frontend-debconf, and ubiquity-ubuntu-artwork, and ubiquity-casper, just to give you an idea of what installs and uninstalls when using the terminal to add/remove it over and over. And they are all the latest ubiquity versions: ubiquity_2.0.10 that are in the repos.

Additionally, I've actually reinstalled Ubuntu Karmic entirely from scratch and on a brand new/freshly erased hard drive, just to see if it was some sort of junk over the many months of Karmic usage, but still, that did not fix the solution.

So as it stands, since something as simple as Ubiquity isn't working, ie the Live CD Installer, I am unable to make a backup of my Ubuntu Karmic laptop and actually be able to reinstall it as well as install on multiple machines.

---

### Post by inameiname on 2010-02-17
Finally, after lots of testings and analysis, I have figured out the problem. It is indeed a PPA repository that had some sort of update which messed with 'ubiquity'. So what I did was reinstalled the entire computer again, but then went through each PPA to see which was causing the problem. 

There is something updated about two weeks ago or so in the following which conflicts with 'ubiquity' (as well as 'nautilus-actions' too actually) which will mess it up to the point where it cannot even open, thus not being able to back up:

deb [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) karmic main 

So to those who have a similar problem, I suggest checking to see if you have 'janvitus' repository in your sources.list.

Woosh, boy to I feel better now. :P Thanks for all those that have tried to help, which allowed me to deduce some things to get to the point that I was to be able to find the problem.

---

