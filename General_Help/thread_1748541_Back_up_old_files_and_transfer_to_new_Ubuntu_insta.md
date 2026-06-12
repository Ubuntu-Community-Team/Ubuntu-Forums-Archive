---
title: "Back up old files and transfer to new Ubuntu installation"
date: 2011-05-03
forum: General Help
---

### Post by electrifiedmojo on 2011-05-03
[SIZE=2]I want to back up files from my current Ubuntu installation to cd/dvd and reinstall the latest version of Ubuntu.. and then copy my old files over into the new installation... I am mostly interested in saving my images, Documents music and Firfox bookmarks but I would like to know how to do a full backup and transfer.... I am a new Ubuntu user 10.10 was my first installation, I am not afraid of terminal CL's but am new to some of the terminology so if someone knows of a tutorial for newbie's it would be very helpful... thank you.
[/SIZE]

---

### Post by Jack9099 on 2011-05-03
Hey, first you'll need to open your CD burner of choice and I think your best option is to copy your Entire Home directory to the CD, or select files individually, also for your firefox stuff I think there's a hidden directory in your home Directory (CTRL+H) your best shot would be to copy that for your bookmarks or write them to a .txt file, hope this helps :D

---

### Post by oldfred on 2011-05-03
You should be backing up everything anyway. After my conversion from 32 bit to 64bit I have only done clean installs, but cheat by just creating a new 25GB / (root) so I still have my old install to go back to if I have to.

backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sql db, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade


I also copy some things that change a lot (most of above from /home) via rsync to another drive, but mostly rely on copies of all data to DVDs. Of course my system is a home system with little value added per week, so I do not feel I have to have a daily, weekly, monthly schedule that a business might need. 

For a new install of a new version, you may not want to recopy everything back as the new versions may be different. This includes sources which are based on version, config settings in /etc, programs from dpkg list that are old/obsolete/not used anymore.

---

### Post by Jack9099 on 2011-05-03
I guess this is what seperates the noobs (like me) and experienced users, This reply is awesome, I'm sure the guy who asked will have everything he needs now :')

---

### Post by Sunships on 2011-05-04
Ditto, I have bookmarked this and will try it out when I next decide to upgrade or mess with something important!

---

### Post by electrifiedmojo on 2011-05-08
Thanks guys..... I am fully restored... it took a couple days because I had some other problems along the way but I finally got it

---

