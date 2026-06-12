---
title: "Need to install stuff."
date: 2010-03-06
forum: General Help
---

### Post by SanjogS on 2010-03-06
I am usin this computer for a few months. It has Ubuntu installed, I like it but I'd like to change a few things.

- I prefer opera, cant install it.
- I want to install a dock.
- This thing has no decent music player, I need one.

I checked few websites but did not understand anything, any help.

---

### Post by howefield on 2010-03-06
> **SanjogS said:**
> 
- I prefer opera, cant install it.

Download the .deb package from opera.com

Double click the file to start it installing.

> - I want to install a dock.

Open Synaptic Package Manager from the System > Administration menu and download either avant-window-navigator or cairo-dock

> - This thing has no decent music player, I need one.

Thing ?

---

### Post by MelDJ on 2010-03-06
for media player: [http://www.ubuntugeek.com/ubuntu-media-players-overview.html](http://www.ubuntugeek.com/ubuntu-media-players-overview.html)
opera: [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)
installing software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by skymera on 2010-03-06
Opera:
```
sudo gedit /etc/apt/sources.list
```
paste this at the bottom of the file:
```
deb http://deb.opera.com/opera/ stable non-free 
```
Save and close the file. Open terminal and enter these, one by one:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install opera 
```

Dock:
```
  sudo apt-get install avant-window-navigator 
```

Music player:

```
 sudo apt-get install banshee 
```

---

### Post by ajgreeny on 2010-03-06
> - This thing has no decent music player, I need one.
You must be joking, or not looking very closely!

There are many many music players for linux and ubuntu, many of which are even better than those I used many moons ago in windows.

Are you missing iTunes?  I have never used that at all, so admit I don't have the ability to compare ubuntu's players with that, but I'm aware that most people seem to very quickly get an alternative such as amarok, rhythmbox, banshee, songbird, etc etc that they love.

---

