---
title: "How to share firefox bookmarks in dual boot"
date: 2009-10-11
forum: General Help
---

### Post by Gryphen on 2009-10-11
First you have to edit your fstab file so that your windows drive automounts. this link isn't an exact guide but it has all the info you need [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) you should have your windows mount point at /media/windows/.

Second open the terminal and type sudo nautilus or if you use kubuntu type gksu dolphin. then change the permissions for your windows drive to your user name.

Third open your windows firefox profile folder [this link tells you where it is]("http://kb.mozillazine.org/Profile_folder_-_Firefox").Then open a new window and go /home/.mozilla/firefox/ make a new folder and name it hybrid.default( or what ever you like). then link the contents of your linux firefox profile folder to the hybrid.default that you made. Then in your windows folder select bookmarks.html, bookmarkbackups, places.sqlite, places.sqlite-journal, and make links in the hybrid.default folder. And last open the profiles.ini file and change the last line to Path=hybrid.default.

Also you should [COLOR=Red]backup your bookmarks[/COLOR] before you do this.

This method is based on [THIS]("http://ubuntuforums.org/showthread.php?t=660251")

---

### Post by wilee-nilee on 2009-10-11
There are several Foxfire add-ons that will do the same thing along with your passwords to any other computer you want as well as a dual boot Xmarks I think is the best.

---

### Post by Gryphen on 2009-10-11
From reading the reviews it seems that many people are unhappy with xmarks.
And my method is more private than xmarks.

---

