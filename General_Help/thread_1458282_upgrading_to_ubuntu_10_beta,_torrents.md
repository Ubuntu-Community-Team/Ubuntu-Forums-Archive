---
title: "upgrading to ubuntu 10 beta, torrents"
date: 2010-04-19
forum: General Help
---

### Post by skibster on 2010-04-19
i want to switch from my current ubuntu 9.10 to ubuntu 10.04 beta, but i am reluctant too because i have deluge running over 500 torrents and i need to continue uploading them. will ubuntu get everything moved over for me? if not, how should i go about doing this?

---

### Post by chris.jericho on 2010-04-19
everything will get moved

---

### Post by skibster on 2010-04-19
ok im trusting you chris haha thanks man

---

### Post by lovinglinux on 2010-04-19
> **chris.jericho said:**
> everything will get moved

In fact, nothing is going to be moved. It will just upgrade your system with new packages. Your personal settings, including deluge torrent state and configurations will be kept.

Keep in mind that 10.04 is still beta and thus can cause you some problems. Although most of the problems have been already fixed, some users still experience issues, including those that prevent the system to boot. So I would recommend asking if anyone else with a similar system had any trouble. See [Lucid Lynx Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=377) forum.

I'm running the Beta 2 fine here.

Also keep in mind that, IMO, upgrades can be more problematic than clean installations. If you want to do a clean install, you will need a separate partition for home in order to keep your settings and files or make a complete backup of your home directory. Backups of important data is recommended in any situation anyway.

---

### Post by skibster on 2010-04-19
yeah mos def nothing got moved.... wish i would have waited for this next post. thank you for replying with your helpful post however, i just did a clean install and im liking it thus far. from now on im backing up all my .torrent files.

---

### Post by lovinglinux on 2010-04-19
> **skibster said:**
> yeah mos def nothing got moved.... wish i would have waited for this next post. thank you for replying with your helpful post however, i just did a clean install and im liking it thus far. from now on im backing up all my .torrent files.

Did you lost everything???? No backups????

Since you have already lost your data, take some time to do a new clean installation, but this time [creating a separate partition for home](http://www.psychocats.net/ubuntu/separatehome). It will save you form a lot of trouble in the future.

---

### Post by chitowner2 on 2010-04-21
I have a similar scenario. Creating a new /home is no big deal. I also have good, current backups of my system. 

But I am running 9.04 with kde 3.5 so I want to do a clean install to a new 10.04 beta2 (to beat the rush!).

I also run ktorrent and the last time I did this, I lost the config file or whatever ktorr uses to keep track of things. How do I preserve whatever I need to allow ktorr to resume?

Thanks
CT  :confused:

---

### Post by lovinglinux on 2010-04-21
> **chitowner2 said:**
> I have a similar scenario. Creating a new /home is no big deal. I also have good, current backups of my system. 

But I am running 9.04 with kde 3.5 so I want to do a clean install to a new 10.04 beta2 (to beat the rush!).

I also run ktorrent and the last time I did this, I lost the config file or whatever ktorr uses to keep track of things. How do I preserve whatever I need to allow ktorr to resume?

Thanks
CT  :confused:

Backup ~/.kde/share/apps/ktorrent and ~/.kde/share/config/ktorrentrc

Your torrent data needs to be backed up too, obviously.

---

### Post by chitowner2 on 2010-04-22
> **lovinglinux said:**
> Backup ~/.kde/share/apps/ktorrent and ~/.kde/share/config/ktorrentrc

Your torrent data needs to be backed up too, obviously.


Thanks for pinpointing those for me. I guess I should browse through the .kde tree and look for other things which will need special treatment.

Everything on my system gets backed up with the exception of a few folders in root and I know that the entire .kde tree is included. But given that I am going to do a clean install of 10.04 and rename the existing /home folder, there will be other things needing special attention as well.

CT

---

### Post by skibster on 2010-04-24
no i did not lose everything! haha im way to careful for that, had it all on an external, just the torrent files themselves so my ratios on the private trackers i am on are gonners ha. i now back up ALL of my torrent files in two different locations.

---

