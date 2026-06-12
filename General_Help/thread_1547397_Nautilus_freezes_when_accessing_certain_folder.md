---
title: "Nautilus freezes when accessing certain folder"
date: 2010-08-06
forum: General Help
---

### Post by Rubicon421 on 2010-08-06
Every time I try to access the .wine folder Nautilus freezes. It may have nothing to do with wine and just be something about that folder or it's contents but here's what I have figure out so far:

-it freezes when double clicking the folder in Nautilus, right clicking, selecting folder next to it then arrow over to select
-does same thing when accessed as root
-everything worked fine when booting from a live CD
-restarting Nautilus or rebooting has no affect
-when it freezes, I can not scroll, select another folder, or do anything else in Nautilus, but it does respond to clicking the close window button by displaying the force quit dialog.

---

### Post by DFlame on 2010-08-06
Hm. What happens when you try to access it via Terminal?

Open a terminal window and try these commands. Post the output if you can :)

```
cd .wine
ls
```

If you aren't using anything irreplaceable in WINE, you could also try removing the package and deleting the folder via terminal, then re-installing:

```
sudo apt-get purge wine
rm -r .wine
sudo apt-get install wine
```

DFlame

---

### Post by Rubicon421 on 2010-08-06
droid-pc@droid-pc-desktop ~ $ cd .wine
droid-pc@droid-pc-desktop ~/.wine $ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg  wine-doors
droid-pc@droid-pc-desktop ~/.wine $ 

Disk Utility reports 1 bad sector on the drive I am having the problem with. There are several partitions on the drive and two other (windows) OSs so the bad sector is not necessarily even in the Linux partition but it is a possible cause I guess. 

I don't need anything in wine so I will uninstall and reinstall then update you with the results.

---

### Post by Rubicon421 on 2010-08-06
Well, I uninstalled Wine and deleted the .wine folder using the terminal and I just realized that the problem is not limited to that folder. I am getting the same results when I try to access the usr folder and media folder in the home directory. Although I did get it to open the usr folder once. 

I'm really starting to think it is related to the bad sector. I am cloning the HD tonight and hopefully I won't have to reinstall.

---

### Post by Rubicon421 on 2010-08-06
how can I run fsck on the linux partition since I can't unmount it? Windows can't see the partition to do a check disk on it so I guess I would have to run it off of a liveCD.

---

### Post by Rubicon421 on 2010-08-06
I don't exactly know why this was affecting it but I fixed it and I think it had something to do with some scripts I installed from here:

[http://mundogeek.net/nautilus-scripts/#nautilus-tag-music](http://mundogeek.net/nautilus-scripts/#nautilus-tag-music)

I installed all of them except the music ones and the problem started shortly after. I decided to uninstall them and see if that did anything and now it works fine.

---

### Post by DFlame on 2010-08-07
Good to hear it's sorted :)

---

