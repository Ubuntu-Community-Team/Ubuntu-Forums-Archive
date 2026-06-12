---
title: "Moving parts of the system for space???"
date: 2011-08-22
forum: General Help
---

### Post by Kallun on 2011-08-22
Uh oh spaghetti-O's!

My system just prompted that I have low disk space... not fun.

So, here's the situation:

I have a 60GB SSD with 10.10 installed on it, I also have a 1TB SATA drive, which is completely blank... are there any means of me maintaining the SSD as the boot partition, but moving anything installed/other parts of the system over to the 1TB drive?

Really would appreciate some help on this, thanks in advance!

---

### Post by seawolf167 on 2011-08-22
Couple options:

1. Take a look at [this link]("https://help.ubuntu.com/community/Partitioning/Home/Moving"). Since most of the things on your system that are taking up your space are probably contained in your /home directory (pictures, videos, downloads, etc.). You can move your entire /home partition to your other drive.

2. You can transfer your "big" files (again, probably pictures, videos, downloads, etc.) to your other drive and use it as a "data" drive. This would require an entry in /etc/fstab to have it mount at boot time (easy, just let us know if this is the route you want to take).

---

### Post by Kallun on 2011-08-22
> **seawolf167 said:**
> Couple options:

1. Take a look at [this link]("https://help.ubuntu.com/community/Partitioning/Home/Moving"). Since most of the things on your system that are taking up your space are probably contained in your /home directory (pictures, videos, downloads, etc.). You can move your entire /home partition to your other drive.

2. You can transfer your "big" files (again, probably pictures, videos, downloads, etc.) to your other drive and use it as a "data" drive. This would require an entry in /etc/fstab to have it mount at boot time (easy, just let us know if this is the route you want to take).

Thanks for the reply seawolf :)

Well, in my case, I don't actually have much in the way of media on my drive at all, I run a home server and just stream anything I want to play, so, I presume what's taking up space must be things I have installed (I understand that might seem a bit ridiculous, but I run steam under Wine, so the games are probably quite large)

I had planned on using the TB drive as a dedicated data drive and was in fact going to mount it as the home partition during the initial installation. My main concern is speed, I purchased the SSD solely to have the system run from that because of the speed advantage. So, am I right in presuming most installed packages are in the 'bin' directory of the root partition? In which case perhaps it'll be every partition but boot that need moving over? 

Apologies for the essay! :P

---

### Post by seawolf167 on 2011-08-22
Packages can install in many different places. However, since you mention Wine games, they will be under 

```
~/.wine/drive_c/
```You can take a look and see how large that file is, maybe you will want to move that partition still 

```
du -hs ~/.wine/drive_c/
```

---

### Post by Kallun on 2011-08-22
> **seawolf167 said:**
> Packages can install in many different places. However, since you mention Wine games, they will be under 

```
~/.wine/drive_c/
```You can take a look and see how large that file is, maybe you will want to move that partition still 

```
du -hs ~/.wine/drive_c/
```

Hmmm, wine is 12GB. Really not sure what could be taking up all this space? This is a brand new system I built last week, so I'm really not sure how I've managed to take up 57GB!? There's barely anything on here?

---

### Post by ajgreeny on 2011-08-22
Have a look in **Disk Usage Analyser**, which should tell you where all the space is being used.

Note that whatever partition/folder you use as the base for the analysis will show a 100% use, so for example, root, if that is the base folder used, will be 100% and within that /home will be a lower %age, as will /var etc etc.  That info will show you which partition/folder is taking up all your space.

---

### Post by cryptotheslow on 2011-08-22
Check the size of /tmp

I nearly killed my system last week opening a 25GB Truecrypt container from my 2nd (large with lots of space) drive. You guessed it Truecrypt likes to hold a copy of it in /tmp - which being in my relatively tiny / filesystem did not go down too well. :D

Now /tmp is happily off on its own much larger partition.

So yes the answer is you can move pretty much any part of your filesystem to the other drive. Just identify what is eating up the space, then use a LiveCD to copy it over and edit /etc/fstab to mount it into the filesystem where it needs to be. Sounds easy said like that and I guess it is - just read up on how to maintain the permissions correctly when moving it and read up on how to change fstab correctly (make a backup of the file before you change it in case you need to revert your changes!).

Try using the Disk Usage Analyser app to see where the space is being used in a GUI way if it pleases.

---

### Post by seawolf167 on 2011-08-22
You can also see what size the directories are on your system by using the command line

```
cd /
sudo du -h --max-depth=1
```

---

