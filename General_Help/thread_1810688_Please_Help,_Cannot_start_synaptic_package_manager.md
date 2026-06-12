---
title: "Please Help, Cannot start synaptic package manager or software center"
date: 2011-07-23
forum: General Help
---

### Post by egkeat on 2011-07-23
This is what I get when trying to start synaptic:

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I admit fooling around with trying to install nautilus elementary, not really knowing what I was doing, and now things are all messed up.:confused:

---

### Post by Quackers on 2011-07-23
Edit your /etc/apt/sources.list.d file and put a "#" at the start of the line(s) with that new repository and save the file, then quit it.
Then try synaptic again.

---

### Post by egkeat on 2011-07-23
Quackers, thanks.
Now what's a quick way getting to the /etc/apt/sources.list.d file?

---

### Post by Quackers on 2011-07-23
```
gksu gedit /etc/apt/sources.list.d
``` and enter your password when asked.
A new window will open showing the contents of that file.
Comment out (add a # at the start) any line(s) with the new ppa.
Click on File > Save
Then File > Quit
Open synaptic and click on Reload in the toolbar.

---

### Post by egkeat on 2011-07-23
Didn't work. I got a red box with a minus:

/etc/apt/sources.list.d is a directory.
Please check that you typed the location correctly and try again.

---

### Post by thefasterblueone on 2011-07-23
Remove the [COLOR="Red"].d[/COLOR] gksu gedit /etc/apt/sources.list

---

### Post by Quackers on 2011-07-23
Sorry, try this :-)
```
gksu gedit /etc/apt/sources.list
``` and enter password.
A window will open up with the contents of sources.list
Comment out (with a # at the start) any line(s) referring to that new ppa.
Then File > save
then File > quit
Then open synaptic and click on Reload.

---

### Post by egkeat on 2011-07-23
Quackers, where do I comment out?

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

---

### Post by Quackers on 2011-07-23
It's not there.
Please navigate to /etc/apt/sources.list.d and post a screenshot of its contents, thanks.

---

### Post by egkeat on 2011-07-23
Okay, how can I post my screenshot?

Sorry for all the questions but I'm really....really still kinda new to this.

---

### Post by Quackers on 2011-07-23
There's an application installed by default called Take Screenshot. Start that and select the area to grab, take screenhot and save to pictures folder. 
In your next reply choose New Reply on the left (NOT quick reply) and scroll down to Manage Attachments. Navigate to Pictures folder and the screenshot and then click on Upload. Leave a few seconds then close that window. Post reply.

---

### Post by egkeat on 2011-07-23
Ok, here it is. (I hope)

---

### Post by Quackers on 2011-07-23
Ok, please right-click on the first file in there (am-monkeyd- etc) and choose properties and then copy the full file name and paste it into your next post.
Do the same with the second file please.

---

### Post by egkeat on 2011-07-23
Ok, I'm going out for a moment, will do when I get back...thanks.

---

### Post by Quackers on 2011-07-23
Well when you get back try opening a terminal and running ```
sudo rm /etc/apt/sources.list.d/yourfilenamehere.list
```then try synaptic again.

---

### Post by egkeat on 2011-07-23
Yep. That did it! Many thanks!

---

