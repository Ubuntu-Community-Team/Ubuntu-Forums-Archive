---
title: "ppa erro ubuntu 10.10 still not fixed"
date: 2011-03-19
forum: General Help
---

### Post by cazazo on 2011-03-19
Annoying error with the ppa when updating, I did many searches and tried to change the server (Administration>>Software Sources>>Select best server)... and other fixes but didn't work.
Any one had that fixed?

Here is the error so far:


Fetched 4,933B in 7s (644B/s)                                                                                                      
W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ~Plue on 2011-03-19
check if that unspecified ppa is in the /etc/apt/sources.list.d/ directory 
*ls /etc/apt/sources.list.d/*

---

### Post by cazazo on 2011-03-19
> **~Plue said:**
> check if that unspecified ppa is in the /etc/apt/sources.list.d/ directory 
*ls /etc/apt/sources.list.d/*
They don't seem to be there. 
The output is:

banshee-team-ppa-maverick.list          
google-talkplugin.list                 
skype.list
banshee-team-ppa-maverick.list.save     
google-talkplugin.list.save            
skype.list.save
cairo-dock-team-ppa-maverick.list       
gwibber-daily-ppa-maverick.list.save   
tualatrix-ppa-maverick.list
cairo-dock-team-ppa-maverick.list.save  
libreoffice-ppa-maverick.list.save     
tualatrix-ppa-maverick.list.save
elegant-gnome-ppa-maverick.list         
local-repository.list                  
user-ppa-name-maverick.list
elegant-gnome-ppa-maverick.list.save    
local-repository.list.save             
user-ppa-name-maverick.list.save
google-chrome.list                      
screenlets-dev-ppa-maverick.list       
virtualbox-offical-source.list
google-chrome.list.save                 
screenlets-dev-ppa-maverick.list.save  
virtualbox-offical-source.list.save

---

### Post by ~Plue on 2011-03-19
> **cazazo said:**
> They don't seem to be there. 

i'll take a guess it's there :)
> **cazazo said:**
> 
local-repository.list                  
user-ppa-name-maverick.list
local-repository.list.save             
user-ppa-name-maverick.list.save

sudo rm /etc/apt/sources.list.d/user-ppa-name-maverick*

and if the local-repository.list doesn't have anything,
sudo rm /etc/apt/sources.list.d/local-repository*

after that, *sudo apt-get update*

btw, i'm not sure whether skype has a repository setup for amd64, so you might need to delete that too to get rid of the errors

---

### Post by cazazo on 2011-03-19
> **~Plue said:**
> i'll take a guess it's there :)


sudo rm /etc/apt/sources.list.d/user-ppa-name-maverick*

and if the local-repository.list doesn't have anything,
sudo rm /etc/apt/sources.list.d/local-repository*

after that, *sudo apt-get update*

btw, i'm not sure whether skype has a repository setup for amd64, so you might need to delete that too to get rid of the errors
Thank you for your help!!! no more errors!!!

Forgive my ignorance... I know I've removed them from the source list, does it means that those packages will no longer upgradeable? Or just the ppas were broken?

---

### Post by ~Plue on 2011-03-19
glad you got it solved ;)

a ppa called 'ppa-name' definitely doesn't exist and skype doesn't seem to have an amd64 repo, so they could be called broken i suppose....

---

