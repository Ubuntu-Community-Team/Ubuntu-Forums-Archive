---
title: "XBMC install? Can't find ~/.xbmc/plugins/programs directory?"
date: 2010-06-30
forum: General Help
---

### Post by sastusbulbas on 2010-06-30
I am trying to add XBMC to Ubuntu, as can be seen below it looks straight forward but I have an issue, I cannot find anywhere as described for extracting XBMC add ons? When I click on extract it states extract here IE in my download folder, after switching XBMC on and off I still cant see any folder as described for extracting files to?

Adding the XBMC SVN Repo Installer

In Ubuntu the SVN Repositories are not automatically added. You must add them manually.

    * First, download the SVN Repo Installer from:
    * [http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip](http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip)
    * Extract it to the ~/.xbmc/plugins/programs directory. If this directory does not exist, run XBMC one time and then exit back to Ubuntu. The directory should now exist.
    * Select XBMC Media Center: Applications -> Sound & Video -> XBMC Media Center
    * Scroll down to Programs.
    * Select program plugins.
    * Select SVN Repo Installer
    * Select xbmc-addons
    * Select plugins
    * Choose the plugins that you want to add (i.e., videos)

---

### Post by steveneddy on 2010-07-04
[http://forum.xbmc.org/](http://forum.xbmc.org/)

---

### Post by rlhanson on 2011-02-08
> **sastusbulbas said:**
> I am trying to add XBMC to Ubuntu, as can be seen below it looks straight forward but I have an issue, I cannot find anywhere as described for extracting XBMC add ons? When I click on extract it states extract here IE in my download folder, after switching XBMC on and off I still cant see any folder as described for extracting files to?

Adding the XBMC SVN Repo Installer

In Ubuntu the SVN Repositories are not automatically added. You must add them manually.

    * First, download the SVN Repo Installer from:
    * [http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip](http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip)
    * Extract it to the ~/.xbmc/plugins/programs directory. If this directory does not exist, run XBMC one time and then exit back to Ubuntu. The directory should now exist.
    * Select XBMC Media Center: Applications -> Sound & Video -> XBMC Media Center
    * Scroll down to Programs.
    * Select program plugins.
    * Select SVN Repo Installer
    * Select xbmc-addons
    * Select plugins
    * Choose the plugins that you want to add (i.e., videos)
Has anybody experienced this problem? After the one time start-close of the dashboard I get the message '/xbmc/plugins/programs is not direcory' therefore I can't extract the XBMC SVN Repo Installer and I have no plugins.

---

### Post by timgood on 2011-02-08
Folders that start with a . (full stop, period etc.)are hidden in Ubuntu. To see them from within Nautilus (the file manager), you press CTRL+H 

The folder you need to extract to is called .xbmc/plugins/programs (note the full stop before xmbc!) and if you try to extract to a folder without the full stop in front then you will not get anywhere.

Hope this helps.

---

### Post by rlhanson on 2011-02-08
> **timgood said:**
> Folders that start with a . (full stop, period etc.)are hidden in Ubuntu. To see them from within Nautilus (the file manager), you press CTRL+H 

The folder you need to extract to is called .xbmc/plugins/programs (note the full stop before xmbc!) and if you try to extract to a folder without the full stop in front then you will not get anywhere.

Hope this helps.
I'm running Ubuntu 10.04 64 bit by the way. Now to get back to the problem at hand. When I do the cntrl -H bit and search for .xbmc/plugins/programs it still doesent show up. The search locates 5 files with .xbmc in the labels but they are in the add-on folder.Xbmc seems to run fine. I can run video from the CD player and the on line video streams but I can't install any plugins. I have done a lot of research and have downloaded what I feel is pertinent install data but I haven't run across any fixes that fit my particular proiblem. I sure would like to hear from someone who has fixed the problem.

---

### Post by timgood on 2011-02-09
Why not simply create the folder? Then extract the files there? This would seem to be the easiest way. 

To create a new folder you can right click and select 'create folder'. If you don't have the .xbmc folder create it. If you do, then create the other folders within it.

There is also a lot of help available on the XBMC forum [here]("http://forum.xbmc.org/").

---

### Post by rubylaser on 2011-02-09
Are you trying to Run XBMC Dharma or actually from the SVN?  I would really suggest just running Dharma at this point.  Also, the new folder structure for XBMC puts your addons (plugins) in ~/.xbmc/addons.

If you actually want to run SVN here are some steps to step it up so you can manage it via apt-get...
First install the Helper Tool used when compiling applications and libraries.

```
sudo apt-get install python-software-properties pkg-config
```
Now make your choice if you would like to install the 1. pvr-testing2 (unstable), 2. ppa (nightly) or 3. XBMC stable release. I've used SVN for a while now.

```
1. sudo add-apt-repository ppa:henningpingel/xbmc
2. sudo add-apt-repository ppa:team-xbmc-svn/ppa
3. sudo add-apt-repository ppa:team-xbmc
```
Let's make a system update.

```
sudo apt-get update
```
Then we install the needed applications. (X server, Admin package for Also&OSS, Alsa driver configuration, Binutils, GGC, Power managment, udisk, policykit, XBMC audio)

```
sudo apt-get install xbmc xinit x11-xserver-utils linux-sound-base alsa-base alsa-utils binutils gcc upower udisks pm-utils policykit
```

As, I said before I would suggest XBMC stable at this point.  And you addons will go into ~/.xbmc/addons 

Good luck

---

### Post by rubylaser on 2011-02-09
Also, if this is a desktop install, you might have problems with audio pulseaudio if you're trying to output via hdmi or passthrough.

---

