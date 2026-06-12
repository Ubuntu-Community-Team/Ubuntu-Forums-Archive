---
title: "I want Ubuntu to fly"
date: 2010-05-03
forum: General Help
---

### Post by klemes on 2010-05-03
Well I have run Lucid Lynx since beta1 and up to a point of it's gradual upgrading I had experienced those tremendously low booting times (<15 sec,maybe even less than 10 sec judged subjectively)that other users report.But somehow smewhere in the process of continuous upgrades my boot times went up and up.Now as you can see from my boot-chart I have to wait ~35 sec for a full boot to GDM and I consider this to be very low performance compared to what others are getting.
So I was wondering if anyone could have a look at my boot-chart and give me any suggestions as to what is keeping my boot times from being normal for this Ubuntu release compared to average boot-times other users are getting.
Is someone could shed some light in this I would greatly appreciate it.:popcorn:

---

### Post by dino99 on 2010-05-03
so since b1 you got so many updates, time to time its a good idea to clean the system, make room and reconfigure it.

install gconf-cleaner and use it (yes to all)

be sure you only use lucid genuine repo

sudo apt-get update 
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

metacity --replace

get more room by installing bleachbit

---

### Post by john newbuntu on 2010-05-03
Can't decipher that chart properly.  If you suspect it to be ureadahead, try this if you have not already done so.  As keybuk points out in this post, try forcing a reprofile.  He says: "To force a reprofile, simply remove the "pack" files in  /var/lib/ureadahead and reboot"
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by klemes on 2010-05-03
Wow!Thanks for all the suggestions .I will do all of those things you suggested and report back.

---

