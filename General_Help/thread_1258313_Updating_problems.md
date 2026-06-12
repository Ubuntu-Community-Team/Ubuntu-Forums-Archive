---
title: "Updating problems"
date: 2009-09-04
forum: General Help
---

### Post by Shiv4m on 2009-09-04
I've been getting this little light bulb icon on my taskbar and I think it's about the dead links in my list. I don't know how to get rid of it, but here are the screenshots:

[IMG]http://img30.imageshack.us/img30/6788/screenshotsynaptic.png[/IMG]

---

### Post by drs305 on 2009-09-04
Import the key for virtualbox with:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6DFBCBAE

```

However, you have references to intrepid, dapper and hardy in your sources.list. You should have only entries for the release you are using.

Edit sources.list with:
```

gksudo gedit /etc/apt/sources.list

```
or post the contents here
or open Synaptic, Settings, Repositories, Third Party, see the ones not referencing your release and click Edit.

---

### Post by |Porsche on 2009-09-04
type from terminal
```
sudo gedit /etc/apt/sources.list
```

comment out the lines that contain those URL's.

When done type

```
sudo apt-get update
```

Note: It seems like they are some repositories for some software that you used at some point or tried to use or are using. So you might want to search for new repositories or delete them if unnecessary.

---

### Post by Shiv4m on 2009-09-04
What do I need and which are garbage?

    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe multiverse
# deb [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy main

#Eternal Lands package repository
# deb [http://ppa.launchpad.net/pjbroad/ppa/ubuntu](http://ppa.launchpad.net/pjbroad/ppa/ubuntu) hardy main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

---

### Post by drs305 on 2009-09-04
Shiv4m,

Are you using Dapper? The desktop version reached its End of Life more than a month ago. The repositories *may* still be available since the server is good for another year and a half. In any case, if you can do an upgrade it is time to do so. Here is a link to go from Dapper to Hardy.
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

You should first clean up your sources.list to at least reference only Dapper (assuming you are using Dapper). I've commented out all references to other releases. 

Make a copy of your current sources.list, then open it for editing and replace your current sources.list contents with these. You can also just delete everything beginning in [COLOR="Red"]red[/COLOR] if you prefer.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
gksudo gedit /etc/apt/sources.list

```

> 
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
[COLOR="Red"][B]# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe multiverse
# deb [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy main

#Eternal Lands package repository
# deb [http://ppa.launchpad.net/pjbroad/ppa/ubuntu](http://ppa.launchpad.net/pjbroad/ppa/ubuntu) hardy main
#deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free [/B]
[/COLOR]


---

### Post by Shiv4m on 2009-09-09
Alright after following everything carefully, I still get the error messages. Let me show you all the screenshots I took leading to the problems:

Theres a little light bulb on the top right corner of my taskbar and it's saying the following: [IMG]http://http://img42.imageshack.us/img42/4892/screenshotupdatenotifie.png[/IMG]

When I click on "Run this action now" I get the little download window. It always stops at 67/70: [IMG]http://img17.imageshack.us/img17/2140/screenshotdownloadingpa.png[/IMG]

This is the error I get after waiting a few minutes for the 67/70 to pass: [IMG]http://img29.imageshack.us/img29/6788/screenshotsynaptic.png[/IMG]

Can anyone tell me what to do specifically? I've been having trouble with this for quite a long time and would like to get rid of it so I can finally update. 

Thank you.

EDIT: I read the above post and switched to Herdy and looks like the light bulb is gone, I just hope it doesn't give me anymore errors.

---

### Post by Shiv4m on 2009-09-12
Got the problem once again after switching to Hardy:

[IMG]http://img9.imageshack.us/img9/6788/screenshotsynaptic.png[/IMG]

---

### Post by drs305 on 2009-09-13
> **Shiv4m said:**
> Got the problem once again after switching to Hardy:

You still have some references to dapper in your sources.list.
Post your sources.list and also the results of the other two commands. The first confirms you are now running Hardy and the last looks to see if you have any additional repository sources.
```

lsb_release -a
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d

```

Also, with the problems you have had, I would recommend going into Synaptic > Settings > Repositories Authentication and removing any entries you have there for mulx.net. There are problems with the keys you have for that repository, so removing them and then adding them again should clear *that* problem. You will add them the next time you run an update and get the error messages stating you don't have the "public key". Post the error message and we can show you the command to run.

---

### Post by Shiv4m on 2009-09-13
Okay removed all the dapper and mulx.net repo in Synaptics and it worked, no errors at all.

---

