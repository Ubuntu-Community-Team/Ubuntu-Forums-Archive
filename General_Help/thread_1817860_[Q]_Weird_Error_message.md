---
title: "[Q] Weird Error message"
date: 2011-08-03
forum: General Help
---

### Post by waltercln on 2011-08-03
Hello, new here. I have been using ubuntu for a day so far and love it! never going back to windows. However, I am new here and I am having a bit of trouble installing some stuff and i keep getting this error. If anyone could point to the right direction in order to fix this i would highly appreciate the help. Here is a picture of what I am talking about. 

[http://imageshack.us/photo/my-images/688/screenshotqig.png/](http://imageshack.us/photo/my-images/688/screenshotqig.png/)

I want to install VLC and i keep running into this problem, sometimes it just pops up as well.


also getting this little error at the top of my screen. 

[http://imageshack.us/photo/my-images/9/screenshot1bl.png/](http://imageshack.us/photo/my-images/9/screenshot1bl.png/)


also the ubuntu software center is just unusable, all it does is load and never displays anything?

---

### Post by wildmanne39 on 2011-08-03
Hi, the problem is your apt-get is broken at the moment please run this command in a terminal and post the out come here
```
sudo apt-get update
```
by clicking on new reply and click # and paste the information between the brackets.

---

### Post by thefasterblueone on 2011-08-03
Copy and paste this command in Terminal and post the results.

```
cat /etc/apt/sources.list
```

---

### Post by waltercln on 2011-08-04
> **wildmanne39 said:**
> Hi, the problem is your apt-get is broken at the moment please run this command in a terminal and post the out come here
```
sudo apt-get update
```
by clicking on new reply and click # and paste the information between the brackets.

thanks for your reply, this is what i get. 

```
walter@ubuntu:~$ sudo apt-get update
[sudo] password for walter: 
E: Type 'Reading' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```








> **thefasterblueone said:**
> Copy and paste this command in Terminal and post the results.

```
cat /etc/apt/sources.list
```



thanks for your reply. this is what comes up and i have no idea what to do next? 


```
walter@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://download.tuxfamily.org/glxdock/repository/ubuntu natty cairo-dock ## Cairo-Dock-Stable
Reading package lists...
Building dependency tree...
Reading state information...
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
```

---

### Post by oldos2er on 2011-08-04
Somehow you've gotten bogus text in your sources.list. Run ```
gksu gedit /etc/apt/sources.list
``` and remove the lines 

Reading package lists...
Building dependency tree...
Reading state information...

Save and exit, rerun ```
sudo apt-get update
``` If there are any more errors, please post them here.

---

### Post by plucky on 2011-08-04
Also put a # in front of ```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
``` as you don't want it asking for the install CD whenever you are installing software.

Also I would recommend doing the same for ```
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
``` as that repository could install updates that might break your operating system.

Good Luck

---

### Post by The Cog on 2011-08-04
I agree with oldos2er. The lines to remove are near the end. Leave the last two lines in the file (starting with "deb "), but remove the three before that.

---

### Post by waltercln on 2011-08-04
thank you all for taking the time to assist me. After i followed the directions from oldos2er and plucky the system checked for updates and there was a whole bunch to update. Restarted and everything is PERFECT now, ubuntu software center is working now. Thanks a million!

---

