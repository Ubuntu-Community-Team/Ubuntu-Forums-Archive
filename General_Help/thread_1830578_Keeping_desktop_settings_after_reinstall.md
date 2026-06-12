---
title: "Keeping desktop settings after reinstall?"
date: 2011-08-21
forum: General Help
---

### Post by jatwood on 2011-08-21
Hi everyone,

Which folders hold the user desktop settings?

The following folders appear to be important, but I wanted to make sure:

/home/user/.gnome2/panel2.d/default/launchers
/home/user/.icons
/home/user/.themes/20110629
/home/user/.fonts

Are there any other folders that I'm missing? 

I'm pretty picky about the placement of my launchers and the folders that I have, fonts, etc.

I'm using Ubuntu 10.04  with Gnome.

---

### Post by L a r r y on 2011-08-22
/home contains a /home//lost+found and a /home/(username1), and if there are other users on the machine, their home folders will be in the /home/(their-username) folder.

To keep your settings from one install to another, it is best to place /home in a separate drive partition from the operating system.  You can copy your /home into another partition prior to reinstall.  There are tutorials for moving /home.  I usually do a Google search for "ubuntu  _____" filling in the blank with whatever search terms I need.

---

### Post by jatwood on 2011-08-22
Hi,

I actually have a separate /home partition.  Whenever I do a reinstall, all of my settings are retained; however, I was more concerned specifically with which folders actually hold the user's desktop settings.

I have a lot of "junk" in my home folder that I would like to delete, but I need to know which user setting folders are crucial, and which ones are not.

---

### Post by Script Warlock on 2011-08-22
to name a few of the files you should keep are: dots cache, compiz,config, dbus, fontconfig, gconf, gconfd, gnome2 ,gnome2_private, g-streamer0.10, gvfs, icedtea, icons, macromedia, mozilla, nautilus, pki, pulse, themes, thumbnails, bashes, xsessions and some etcs..

---

### Post by jatwood on 2011-08-22
^Thanks, I think that I now have a good idea of the folders that are critical to user settings and which ones are not.

---

