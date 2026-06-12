---
title: "Issues with new Natty build"
date: 2011-05-10
forum: General Help
---

### Post by Decon1986 on 2011-05-10
First and foremost, Unity is a nice interface and I can see why Canonical wants to move in that direction to capture a new user base. With that said, I don't yet fully appreciate the loss of customization sacrificed for the new user base.

I tried getting emerald to decorate my windows with the old "simple glass" theme I had carried over from Hardy Heron. That did not work. I saw this ***_[fix]("http://ubuntuforums.org/showthread.php?t=1702253")_*** but I would rather wait until I don't have rely on someone else's text file. I also experienced the disappearing window-borders issue when attempting to set emerald through ccsm.

When I tried to get the cube working in unity with this _***[fix]("http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/")***_, I had it working for a second and then it broke all my settings. I will attempt this *_**[fix]("http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/")**_* next. Before this, I crashed my new install at least twice and had to reinstall completely, not to mention I had to fix registry and bootup for wubi before even getting to the point where I could crash it. The only reason I did a clean install was because during the upgrade, I closed the lid, and it killed the system; it had recovered the first time I closed the lid, gave me a black screen with blinking cursor the second time, whereupon I did a manual shut-off and saw the update screen flash at me as it shut off. I had to manually remove my ubuntu install from vista after that, causing all kinds of trouble for the next wubi install, so I had to go back and clean it up to finish installing it properly and ensure that I could cleanly uninstall.

Finally, wallpaper-tray. I got it working by downloading the binary package from the old ***_[]("https://launchpad.net/ubuntu/+source/wallpaper-tray/0.4.6-5")[version 0.4.6-5 ]("https://launchpad.net/ubuntu/+source/wallpaper-tray/0.4.6-5")[of wallpaper-tray]("https://launchpad.net/ubuntu/+source/wallpaper-tray/0.4.6-5")_***. But it still crashes occasionally and I had to go into gconf-editor to manually set the values after I was unable to make the settings window appear after the first open. I found no other way to interact with the wallpaper-tray settings; the unity interface did not support interacting with the wallpaer-tray or fusion-icon through simple right-clicks. I tried other wallpaper programs, but they all had the same problem of not being able to right-click on their respective icons or easily interact with the settings. That made me stick with the much simpler wallpaper-tray I knew since Hardy Heron.

Right now, I have avant-window-navigator and the unity dock on autohide and intellihide. That, so far, has been working fine for me, although I do keep crashing things when twiddling with ccsm. I want to stick with the unity interface because I want to be able to evangelize new users, most likely my new students and anyone else who uses the computer lab I will soon be in charge of. I hope some of these issues can be more easily resolved in future updates.

---

