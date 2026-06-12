---
title: "Really need help uninstalling VMware."
date: 2010-10-30
forum: General Help
---

### Post by DesiredFour on 2010-10-30
Soo... I'm a linux newb. Love linux, just frustrated trying to install VMware.

What I've done...

Tried to install vmware player. It worked, used it, shut down. Next time I boot up, I get the infamous message that it needs to load modules and fails. So I go to uninstall vmware-but how? The first step I did was to run
```
sudo -r -rm /etc/vmware
```
or something of the likes. No luck. I then run 
```
sudo vmware-installer -u vmware-player
```
and boom! Success! But then, to my dismay, the uninstaller tells me that it cannot shut down all virtual machines, and that if I have any ACE VM's running I should shut them down and hit retry.

Really have no idea what to do here..

P.S. This is my first post on ubuntuforums.org, I know, its really not contributing, and sorry if this is the wrong section.

---

