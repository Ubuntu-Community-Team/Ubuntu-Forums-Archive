---
title: "Uh oh...."
date: 2006-04-27
forum: General Help
---

### Post by tekwerx on 2006-04-27
OK, was using the old 5.04 guide to setting up my Ubuntu.  Set up the repositories, only to find out "mirrormax" was out of commission.  NP, I stumbled onto thw WIKI and set replaced it all to fix it to where it was to be, and ...well...something broke.  I did "sudo apt-get update" and all was well, then I did "sudo apt-get upgrade" and now I get:

Setting up apt-utils (0.6.40.1ubuntu10) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing apt-utils (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.4-apt:
 python2.4-apt depends on libapt-inst-libc6.3-6-1.1; however:
  Package libapt-inst-libc6.3-6-1.1 is not installed.
  Package apt-utils which provides libapt-inst-libc6.3-6-1.1 is not configured y et.
dpkg: error processing python2.4-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on python2.4-apt (>= 0.6.12); however:
  Package python2.4-apt is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apt:
 python-apt depends on python2.4-apt; however:
  Package python2.4-apt is not configured yet.
dpkg: error processing python-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-apt (>= 0.6.14); however:
  Package python-apt is not configured yet.
 update-manager depends on python2.4-apt (>= 0.6.14); however:
  Package python2.4-apt is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apt-utils
 python2.4-apt
 language-selector
 python-apt
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)



How do I fix this?  Im sure its something easy; Im just a light intermediate at Linux, so I dont know how to fix this yet.  Im finally permanently switching from Windows.  Last night I got an unwanted download from MS (their "Certified OS" download - to verify I am not a pirate).  Well, all of a sudden I find out my copy of Winblows that came with my laptop isnt "legal" any more, and i need to contace MS and buy a new license.  I call them, and let them know that I have the sticker right here on the bottom of the machine, but they say "Sorry, its in our database as being an illegal Key.  How would you like to pay for your new one?"  I just hung up flabberghasted.  Anyhow, and needless to say, Im finally done.  Screw games, I dont like being treated as a thief.  Besides.  Ubuntu is more stable, faster, and free.  :) 
Sorry for my rant....had to get it off my chest.  Anyone know how to fix this?  LoL  Thanks in advance.

---

### Post by tekwerx on 2006-04-27
OK, just did some poking and i cant update or install ANYTHING at all till this gets fixed.  Apparently, it does a check on this stuff first.  Thanks again....

---

### Post by echo $USER on 2006-04-27
> sudo gedit /etc/apt/sources.list

Delete everything in it, replace it with

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

then run 

> sudo apt-get update

---

### Post by tekwerx on 2006-04-27
Thats the exact same one I have...thanks though.  Replaced it all anyhow, and nothing.  It still gives the exact same errors.  Is there any way to fix the errors and start over or something?

---

### Post by Ramses de Norre on 2006-04-27
I'd cut out the us. part when you don't live in the united states.

---

### Post by Ramses de Norre on 2006-04-27
Couple things to try: ```
sudo apt-get -f install
sudo apt-get clean && sudo apt-get remove apt-utils python2.4-apt language-selector python-apt update-manager && sudo apt-get install apt-utils python2.4-apt language-selector python-apt update-manager
sudo dpkg --configure apt-utils python2.4-apt language-selector python-apt update-manager -a
```

---

