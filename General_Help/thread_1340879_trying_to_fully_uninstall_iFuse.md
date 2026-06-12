---
title: "trying to fully uninstall iFuse"
date: 2009-11-29
forum: General Help
---

### Post by GnubbyaBush on 2009-11-29
Hi all i tried to install iFuse on my jaunty 9.04 ubuntu comp, but it was erroring and became too much of a hasle due to the fact im runing x64. So this website is what i did 
 
[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)
 
I uninstalled ifuse using the synaptic package manager, but i don't quite know how to delete the gpd key, the following was how it was installed:
 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
 
also it made me get a program called update..but synapitic manager only shows update-inetd. so not to sure how to uninstall this, it was installed using the following command:
 
sudo apt-get update
 
PS: i know this is fairly strait forward, but i actually tried to search for how to delete these changes and got no where. I know some ppl wouldn't care about these minimal files but this is a server and i try to keep it clean. Thanks if you can help!! :p

---

### Post by ibuclaw on 2009-11-29
To undo everything you did:
```
gksu gedit /etc/apt/sources.list
```
**Remove** the following lines:
```
deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
```
Save and quit.

Delete the key you imported:
```
sudo apt-key del F0876AC9
```
Update your sources:
```
sudo apt-get update
```
Purge ifuse
```
sudo apt-get purge ifuse
```

And you are done!

Regards
Iain

---

### Post by GnubbyaBush on 2009-11-29
danks man, u guys are the best

---

### Post by GnubbyaBush on 2009-11-29
hey  sorry i marked this as solved then realized i wasn't compleltly done, so now this will prob never be seen haha. 
 
when i did the "sudo apt-get purge ifuse" it told me a list of files that where autoinstalled and not needed anymore. It  told me to use apt-get autoremove...but i used synaptic to remove them.
 
 Its all done now but just wondering is synaptics uninstall the same as apt-get autoremove, or is one a bit better than the other?

---

### Post by ibuclaw on 2009-11-29
> **GnubbyaBush said:**
> hey  sorry i marked this as solved then realized i wasn't compleltly done, so now this will prob never be seen haha. 
 
when i did the "sudo apt-get purge ifuse" it told me a list of files that where autoinstalled and not needed anymore. It  told me to use apt-get autoremove...but i used synaptic to remove them.
 
 Its all done now but just wondering is synaptics uninstall the same as apt-get autoremove, or is one a bit better than the other?

apt-get autoremove is a more automatic way of doing it.

In synaptic, did you select all packages manually?

---

