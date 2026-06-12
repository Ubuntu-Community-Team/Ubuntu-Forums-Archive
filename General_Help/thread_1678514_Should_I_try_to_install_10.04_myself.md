---
title: "Should I try to install 10.04 myself?"
date: 2011-01-30
forum: General Help
---

### Post by Extreedoc on 2011-01-30
I have to install Lucid as my old Ibex is way out of date and developing problems. I have two hard drives on my computer, one has XP on it and the other has the Ubuntu. At boot I get a screen offering choices as to which OP to choose. Ubuntu is set as default. Should I, a non techy type try to install Lucid myself. I would like to but never having installed an OP before, especially Linux, I wonder to myself, am I biting off more than I can chew? Should I get help or what?

---

### Post by sikander3786 on 2011-01-30
For everything, there is always a "first time" ;-)

Installing Ubuntu is not a difficult task specially when it comes with a nice GUI installer. The only thing I'll be concerned about is the data on your internal HDD. If there is something important, back it up to an external drive before attempting installation so in case anything goes wrong, it doesn't cost you much.

There are many members around here and we'll try to guide you step by step if you plan to install 10.04. The first step, have you got the installation media? You can use a CD-ROM disc or a USB drive.

And have you got some experience with hardware? I would advise to unplug your Windows HDD before installation as you'll be on the safer side then. And is there anything important on your Ubuntu partition/drive? You'll need to format that.

---

### Post by Extreedoc on 2011-01-30
Hello Sikander, good to hear from you. In answer to your questions, yes, I have a CD, I have backed up all my personal files onto an external HD except for my Bookmarks and my email contacts, I don't know how to back up or export these and as there are quite a few of them I think I should save them somehow, but how?

---

### Post by sikander3786 on 2011-01-30
If the bookmarks are in Firefox, go to Bookmarks > Organize Bookmarks > Import & Backup > Backup. And which email client were you using?

---

### Post by Extreedoc on 2011-01-30
> **sikander3786 said:**
> If the bookmarks are in Firefox, go to Bookmarks > Organize Bookmarks > Import & Backup > Backup. And which email client were you using?

And when I get to "backup" I can choose where to backup to?

I am using Evolution.

---

### Post by sikander3786 on 2011-01-30
Yes you can either choose the location for Backup of bookmarks or move the backup file to a safe place after it is created.

For backing up Evolution, this might help.

[http://library.gnome.org/users/evolution/stable/b17qy921.html.en](http://library.gnome.org/users/evolution/stable/b17qy921.html.en)

I haven't used Evolution myself so can't be helpful there. I Googled and found that link.

---

### Post by davepoth on 2011-01-30
Would it be an easier idea to just upgrade in steps?

---

### Post by sikander3786 on 2011-01-30
I don't think so. Upgrades are known to break at some point and cause troubles. However, they also go fine for many users. You may want to try your luck with upgrades. The more the installed software on Ubuntu, the more are troubles there.

A clean install is always faster than an upgrade. I myself am a strong recommender of a clean install.

And for you, it would be a long path from 8.10 > 9.04 > 9.10 > 10.04. I don't know about success chances here.

---

### Post by uRock on 2011-01-30
I full clean install will be much faster and less painful. Test the LiveCD first.

There were many issues for me when I installed 10.04 with older config files in the /home. With a full clean installs it there has been little to do after installing my extraware.

---

### Post by Vaphell on 2011-01-30
I always do a clean install. Usually upgrades work, but some leftovers can sometimes make system behave in unexpected ways.

If you want to backup your whole firefox profile and evolution related stuff unhide hidden objects in filebrowser (ctrl+h) and look around. There will be .mozilla which is your complete firefox configuration and .evolution. .evolution has subfolders addressbook, mail, calendar, etc. so there is a big chance that it stores all stuff there. Simply copy .mozilla and .evolution to external drive to protect them and after a fresh install you can copy them back so ff and evolution can pick them up.

If you decide to go with fresh install, consider creating separate /home partition - this makes upgrade treadmill completely unnecessary. In such configuration you can wipe system files without user data being harmed in any way. During system installation make sure that home partition is properly identified as /home and leave it unformatted (use partition as is, without meddling). That makes any reinstallation a breeze. It's often much faster to fix some grave mistake by reinstall than care about protecting data while having a gun pointed to your head (eg. unbootable system+hardcore deadline=way too much stress).

---

### Post by Extreedoc on 2011-01-30
Thanks, I can try backing up bookmarks without doing too much damage I think. Thanks also for the link, I have printed the page out for future reference.

I have read about people having problems upgrading step by step, upgrade one level, troubleshoot any problems then start again... I think it will be easier and much quicker to clean install and if I learn how to do it myself, it will be so much easier and less daunting next time I have to do it.

---

