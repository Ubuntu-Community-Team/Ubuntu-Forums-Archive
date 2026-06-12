---
title: "What can I safely delete in /var/log and /var/cache?"
date: 2010-08-25
forum: General Help
---

### Post by t0p on 2010-08-25
I have a serious problem with lack of disk space.  I have ordered some hardware which will solve the issue long-term, but in the meantime I need some elbow room.

The disk usage analyzer revealed a lot of room used up in /var/log, and in /var/lib/apt/lists and /var/lib/dpkg/info.  What can I safely get rid of?

---

### Post by inameiname on 2010-08-25
sudo apt-get install bleachbit

It has settings to delete all that you can in 'var' as well as all sorts of things to safely clean up your computer. 

In addition, there is a bleachbit-bonus, available at their website, to delete even more.

---

### Post by oldfred on 2010-08-25
A lot of command line ways to house clean if you prefer:

HOWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes dependencies
 no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependencies
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..
Autoclean cleans up the downloaded archives (.gz or .tar) files used to install things. Autoremove cleans libraries that are no longer needed.
you can run any "apt-get" command predeccesed by the "-s" (simulate) switch

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

# also computer janitor in system-admin
# see grub cleanup to remove old linux versions or use synaptic
# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

---

### Post by t0p on 2010-08-25
Thanks for all tips and links.  When I have the time I will put it into action and report back with any results.

---

