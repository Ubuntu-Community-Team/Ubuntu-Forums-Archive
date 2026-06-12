---
title: "Gedit/Wireless help"
date: 2010-10-20
forum: General Help
---

### Post by jubop on 2010-10-20
Hi everyone,

so after having my Ubuntu 9.04 get all messed up (my fault) really and being to lazy to figure out how to fix my screw-up and figuring I didn't have anything worth saveing that couldn't be easily backed up, I installed karmic on my Lenovo 3000 N100.

The problem is that I can't connect to wireless internet which isn't really a problem since I had the same problem when I installed Karmic on my friend's computer, all I need to do is change the file in /etc/modprobe titled blacklist-ath_pci.conf, the only problem is when I open the file with Gedit and change the line  to #blacklist ath_pci (to disable the blacklisting) I can't save it, if I try to quit then save as and replace the file I am told "you do not have permission to save the file. please check the location and try again"

I know I'm in an admin user account and the preferences for the account are all enabled so have the authority to change the file, if I remember correctly to edit system files you have to go about it a different way then just opening them up and editing them, but it's been so long I just can't remember.

Any help would be greatly appreciated.

---

### Post by Jebtrix on 2010-10-20
gksudo gedit <filepath>

---

### Post by jubop on 2010-10-20
kay so that worked, thanks, except it didn't lol. I was able to successfully unblacklist the driver and save the file, but apparently that wasn't my problem, I've tried checking for hardware drivers but nothing's shown up just says "no proprietary drivers are in use on this system" :( Any suggestions, I'm sure it's compatible with my system I've been running Ubuntu for years now and even ran wireless from the live CD when testing out this distribution for my friend.

---

### Post by Jebtrix on 2010-10-20
Try
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

Since your laptop uses Broadcom BCM94311MCG wifi chip

---

### Post by jubop on 2010-10-21
Thanks, worked perfectly.

---

