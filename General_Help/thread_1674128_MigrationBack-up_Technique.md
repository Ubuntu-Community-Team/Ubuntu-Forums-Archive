---
title: "Migration/Back-up Technique?"
date: 2011-01-23
forum: General Help
---

### Post by gfunkera on 2011-01-23
can anyone explain the proper methods to successfully back up all settings and data (files, movies, pictures, music... i mean EVERYTHING thats mine) so that one can migrate to another computer/distribution...

what im looking to do is backup all my stuff on an external drive and reformat my hard drive and installing linux all over again...

im having way too many problems with my ubuntu machine as of late...

thanks!

---

### Post by gordintoronto on 2011-01-23
I've done this. My approach:

From accessories/terminal run this command:
dpkg --get-selections "*" > Desktop/applications
It creates a list of everything which is installed, in gruesome detail. After installing a new version of Ubuntu, I edit the list and install the chosen applications with these commands:
sudo apt-get update
sudo dpkg --set-selections < Desktop/applications
sudo apt-get -u dselect-upgrade

I export my favorites from my browser into a file, and "save settings" in Evolution. Then I copy everything from /home, including the hidden folders, onto an external hard drive. When I restore the data, I don't include the hidden folders, I just keep them for possible reference.

---

