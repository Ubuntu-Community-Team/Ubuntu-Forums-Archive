---
title: "Updating a computer lab with limited Internet access"
date: 2011-02-13
forum: General Help
---

### Post by arrrimapirate on 2011-02-13
Hi, I'm a US Peace Corps Volunteer serving in Mongolia. I've been trying to convert our computer labs from Windows to Linux Ubuntu 10.10. The defense against viruses and language support is really a great thing for here. However,I'm kind of stuck. 

I'm really far out in the countryside. Our lab doesn't have computer access. What is the best way to update all the computers so can play all music and video files, and full Mongolian language support for the desktop and Open Office. I've tried, APTonCD, but I always get errors that I am missing dependencies. I'm now trying Keryx, but it also failed on me once. I'm going to try it again when I get to an Internet connection with decent speed (mine is not). Is this the best route? Can anyone recommended anything better. It takes a long time to do these things.

Also, would simply installing Edubuntu solve this problem for me?

---

### Post by Joe of loath on 2011-02-13
Sounds like what you need to do is take a fresh ubuntu install, use apt-get to install everything you need to, and pull all the packages out of /var/apt/cache. Put them on a cd/DVD/usb stick etc, and install what you need from that.

---

### Post by arrrimapirate on 2011-02-15
Okay, is there any reason I need to do a fresh install. Can I do from my personal computer now? I use Ubuntu more than any other OS. Will dependencies not be a problem this way?

Also I can't find the var folder. I've unhidden all of the folders in the home folder.

---

### Post by matt_symes on 2011-02-15
Hi

If you want a different solution, what about downloading the entire repositories and burning them to a number of DVD's. This guide is for dapper but it should work with maverick if you make the changes required.

[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

I believe you can also buy the DVD's. That way you will not have the dependency issues and you will have the entire repositories with all that software to hand wherever you go. I don't know if this is overkill for you but i thought i would chuck it into the mix.

Good work BTW.

Kind regards

---

### Post by stinkeye on 2011-02-15
You can use this script to create a local repo on a usb stick
using an up to date computer of the same release.
If you install all the packages on this computer to be able
to do what you want, you'll be able to install the same packages on the other machines.

```
#!/bin/sh

#
# Script to update Repository
clear

# Get latest versions from internet
echo "*** Get latest versions from internet ***"
sudo apt-get update
sudo apt-get -u upgrade

# Create archive folder on usb stick
echo "*** Create archive folder on usb stick ***"
mkdir [COLOR="Magenta"]/media/85DA-06D2[/COLOR]/archives

# Copy files from cache to repository
echo "*** Copy files from cache to repository ***"
cp /var/cache/apt/archives/*.deb [COLOR="#ff00ff"]/media/85DA-06D2[/COLOR]/archives

#Change to Repository Directory
echo "*** Change to Repository Directory ***"
cd [COLOR="#ff00ff"]/media/85DA-06D2[/COLOR]/archives

# Make Packages.gz file for synaptic
echo "*** Make Packages.gz file for synaptic ***"
sudo apt-get install build-essential
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
echo "*** Repository is up to date ***"

# Edit your /etc/apt/sources.list file.
# gksudo gedit /etc/apt/sources.list
# And insert this on a new line (preferably the first):
# deb file:[COLOR="#ff00ff"]/media/85DA-06D2[/COLOR]/archives/ /
```
Save as **UpdateRepository.sh** in your home directory and make executable.
You will need to change all the [COLOR="Magenta"]highlights[/COLOR] to what nautilus shows you
when pressing ctrl+l while in your usb directory.
The script will download build-essential if it's not installed to build
a Packages.gz that can be used by synaptic.

To create/update the repository, insert your usb stick and run in terminal
```
./UpdateRepository.sh
```


Then add the usb as a repo on the machines to be updated as shown on last 4 lines of the script.

Insert the usb and run
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mikewhatever on 2011-02-15
> **arrrimapirate said:**
> Okay, is there any reason I need to do a fresh install. Can I do from my personal computer now? I use Ubuntu more than any other OS. Will dependencies not be a problem this way?

Also I can't find the var folder. I've unhidden all of the folders in the home folder.

I don't think a fresh install is required. The packages you install are first downloaded to /var/cache/apt/archives, which isn't in the home folder. If AptonCD requires a dependency, it's quite possible that you can find it in that location on your own computer.

---

### Post by Joe of loath on 2011-02-15
the reason i suggested a clean install is that your macine may already have some of te dependencies installed, which mmeans on the freshly installed lab pcs you'll be missing some packages you'll need.

---

