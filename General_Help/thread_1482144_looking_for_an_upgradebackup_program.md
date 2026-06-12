---
title: "looking for an upgrade/backup program"
date: 2010-05-13
forum: General Help
---

### Post by woop on 2010-05-13
basically something that will aid me save all my current files and folders, so that when I wipe 8.10 and reinstall 10.04 

any reccomendations appreciated

---

### Post by warfacegod on 2010-05-13
The easiest way is to simply drag n' drop your Home folder to another HDD or External HDD if you have either.

Howeaver, remastersys or grsync, may be useful to you.

---

### Post by VastOne on 2010-05-13
> **woop said:**
> basically something that will aid me save all my current files and folders, so that when I wipe 8.10 and reinstall 10.04 

any reccomendations appreciated

Follow [_[COLOR="DarkRed"]These[/COLOR]_]("http://www.psychocats.net/ubuntu/separatehome") directions and when you are in the gparted stage of the install, make sure that partition you have created is set as /home and DO NOT FORMAT IT

---

### Post by nmaster on 2010-05-13
i'd suggest this for backing up your system: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

if something goes wrong you can reinstall 8.10 and revert everything back to how it was.

you can also use tar to backup any particular directory. it works well.

---

### Post by warfacegod on 2010-05-13
> **neal.m.master said:**
> i'd suggest this for backing up your system: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

if something goes wrong you can reinstall 8.10 and revert everything back to how it was.

you can also use tar to backup any particular directory. it works well.

A great guide but I've stopped linking it for people because its rather dated and I haven't been able to get it to work 100% for anything higher than 8.04

---

### Post by nmaster on 2010-05-13
> **warfacegod said:**
> A great guide but I've stopped linking it for people because its rather dated and I haven't been able to get it to work 100% for anything higher than 8.04


how can tar not work?


also, you could use partimage to copy the entire drive.  this would be another way to back up your system. [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by warfacegod on 2010-05-13
> how can tar not work?

I'm not exactly sure. I think has something to do with the includes/excludes. I've broken several installs each of Intrepid, Jaunty, and Karmic trying to restore. No problems with Hardy backward.

---

### Post by nmaster on 2010-05-15
> **warfacegod said:**
> I'm not exactly sure. I think has something to do with the includes/excludes. I've broken several installs each of Intrepid, Jaunty, and Karmic trying to restore. No problems with Hardy backward.

that's good to know.  what do you do to make system backups?  apparently partimage doesn't work on ext4, so now i'm not sure what is best.

---

### Post by warfacegod on 2010-05-15
> **neal.m.master said:**
> that's good to know.  what do you do to make system backups?  apparently partimage doesn't work on ext4, so now i'm not sure what is best.

On the rare occasion I want to make a back up my system, I use remastersys.

However, I keep my Home folder on a separate partition. When I do a new install, I only need to spend about 30 minutes reinstalling programs and packages and removing others because all of the user settings are stored in /home.

---

### Post by HandLotion on 2010-05-16
I need to backup lucid in a ext4 partition so I am real disappointed that partimage won't work. I don't find remastersys thru synaptic package manager in Jaunty. Where can I find it and will it backup the entire lucid partition?

---

### Post by warfacegod on 2010-05-16
remastersys isn't available in the repositories. Here's a .deb file of it just rename it and take the .zip off of the end.

---

### Post by scouser73 on 2010-05-16
I'd advise you to install Deja Dup.  Check out the site for instructions and screenshots, by the way it's extremely easy to use. [http://live.gnome.org/DejaDup](http://live.gnome.org/DejaDup)

---

### Post by nmaster on 2010-05-17
you could also look at clonezilla: [http://www.clonezilla.org/](http://www.clonezilla.org/)

---

