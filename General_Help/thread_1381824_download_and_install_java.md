---
title: "download and install java"
date: 2010-01-15
forum: General Help
---

### Post by csckid on 2010-01-15
i used synoptic packet manager to download and install jdk(java). My internet connection is very slow. So each time I format my pc, I need to download jdk( and other software) again using synoptic packet manager. Is there way where I won't need to download jdk each time I format my pc
thanks

---

### Post by Linuxforall on 2010-01-15
> **csckid said:**
> i used synoptic packet manager to download and install jdk(java). My internet connection is very slow. So each time I format my pc, I need to download jdk( and other software) again using synoptic packet manager. Is there way where I won't need to download jdk each time I format my pc
thanks

Install apt on cd and save all your packages to a CD for later use.

---

### Post by Mighty_Joe on 2010-01-15
Another option would be to save the Sun Java Linux binary and use [these instructions]("http://sites.google.com/site/easylinuxtipsproject/java") to install it.

---

### Post by stinkeye on 2010-01-15
> **csckid said:**
> i used synoptic packet manager to download and install jdk(java). My internet connection is very slow. So each time I format my pc, I need to download jdk( and other software) again using synoptic packet manager. Is there way where I won't need to download jdk each time I format my pc
thanks
This shows how to make a local repo [_**[COLOR="DarkRed"]How to build local APT repositories[/COLOR]**_]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/")
This script will create a local repo.

Just create a folder on a usb drive or backup drive.
Copy any .debs you manually downloaded and want to keep, to this directory.
Then run the script, changing the [COLOR="Magenta"]highlighted[/COLOR] parts to your own local_repo directory.
 
This will copy all the deb files from /var/cache/apt/archives/ that you downloaded through synaptic.
```
#!/bin/sh

#
# Script to update Repository
clear
# Get latest versions from internet
echo "*** Get latest versions from internet ***"
sudo apt-get update
sudo apt-get -u upgrade
# Copy files from cache to repository
echo "*** Copy files from cache to repository ***"
cp /var/cache/apt/archives/*.deb [COLOR="Magenta"]/media/UBUP/karmic_local_repo/archives[/COLOR]
#Change to Repository Directory
echo "*** Change to Repository Directory ***"
cd [COLOR="#ff00ff"]/media/UBUP/karmic_local_repo/archives[/COLOR]
# Make Packages.gz file for synaptic
echo "*** Make Packages.gz file for synaptic ***"
sudo apt-get install build-essential
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
echo "*** Repository is up to date ***"


```

Then once  you have a done a reinstall,
Edit your /etc/apt/sources.list file like so:
```
gksudo gedit /etc/apt/sources.list
```

And insert this on a new line (preferably the first):
```
deb file:[COLOR="#ff00ff"]/media/UBUP/karmic_local_repo/archives/ /[/COLOR]
```
Insert your usb or mount your backup drive which contains your local repo.
I then open up synaptic and untick all the other repos just to make sure it doesn't connect to the internet.
You can now update and then upgrade through synaptic or update manager
or
alternatively run this second script:
```
#!/bin/sh

# Edit your /etc/apt/sources.list file like so:
# gksudo gedit /etc/apt/sources.list
# And insert this on a new line (preferably the first):
# deb file:[COLOR="#ff00ff"]/media/UBUP/karmic_local_repo/archives/ /[/COLOR]
# or for usb
# deb file:[COLOR="#ff00ff"]/media/My_Repository/karmic_local_repo/archives/ /[/COLOR]

# This script will update the computer to all the latest versions based on local repository
# Update apt
echo " *** Update apt *** "
sudo apt-get update
# Update Computer with local repository
echo " *** Update Computer with local repository ***"
sudo apt-get upgrade
```

[COLOR="DarkRed"]P.S.[/COLOR] Remember to make the scripts executable.
Right click > properties > permissions > tick execute.

---

