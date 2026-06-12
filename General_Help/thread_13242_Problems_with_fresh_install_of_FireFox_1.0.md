---
title: "Problems with fresh install of FireFox 1.0"
date: 2005-01-29
forum: General Help
---

### Post by Ricapar on 2005-01-29
When I first installed Ubuntu, it came loaded with FireFox 0.9, so I downloaded an installed 1.0.

When I start up FireFox, it starts up, but if I want to open another window of FireFox, I get the message saying that the default profile is already in use.

Also, when I middle click on the page, it tries to load up another page that never seems to work. I don't remember if it did that or not in 0.9. When I middle click a tab though, it does the same, it used to just close the tab.

Thanks in advance for any help

---

### Post by madzzoni on 2005-01-29
Do you install FireFox via Apt/synaptic ?

If not, then you have to delete the /usr/lib/mozilla-firefox dir., before installing the new one.

The best way to install Firefox 1.0 is using apt-get.

Uncomment all the sources (see ubuntuguide.org) in your etc/apt/source.list and do: apt-get update

---

### Post by Ricapar on 2005-01-29
I did remove that directory before I installed 1.0, maybe I messed up on something else. I'll try again using apt-get, and post the results in a bit.

---

### Post by Ricapar on 2005-01-29
Ack.. Installed using apt-get, it's at version 0.9.3 again. But now it's worse, middle click does nothing, and foward and back buttons are grayed out no matter what. Also always loads up about:blank as the home page, instead of Google as I set it in the prefrences  :cry:

---

### Post by wojtek on 2005-01-30
I've installed Firefox 1.0 on Ubuntu twice, without any problem. Download  firefox-1.0.installer.tar.gz , then unpack it to the new separate folder in your home directory.  Go to this folder and as root edit the command ./firefox-installer . You'll see the welcome screen and the rest is obvious. Good luck.

---

### Post by WW on 2005-01-30
jdong has put together a "backports" repository for warty, and it includes the latest Firefox.  Take a look here:
   [http://ubuntuforums.org/showthread.php?t=8486](http://ubuntuforums.org/showthread.php?t=8486)
You could try that instead of installing from the tar file.

---

### Post by Ricapar on 2005-01-31
I used the backports, downloaded and installed Firefox with it, but now I have this when I try to open firefox:
[http://img182.exs.cx/img182/9793/screenshot6bi.png](http://img182.exs.cx/img182/9793/screenshot6bi.png)

---

### Post by Ricapar on 2005-02-01
Nevermind, I got it working now. I don't know what was wrong though...
I reinstalled Ubuntu since I made a few other... mistakes with the root console.

I used the backports and it works fine now.

Thanks for the help.

---

### Post by sard on 2005-02-08
Isn't there a repository with the newest version of Firefox?  I've been messing about with Vidalinux ( [http://desktop.vidalinux.com/](http://desktop.vidalinux.com/) ) which is Gentoo based, I hate waiting hours for stuff to compile but at least all the apps are up to date.

---

### Post by frijolito on 2005-02-09
[QUOTE=Ricapar]
I reinstalled Ubuntu since I made a few other... mistakes with the root console.
[/QUOTE]
Now *that* made me spill my drink!

---

