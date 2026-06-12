---
title: "looking for HDD Backup Software"
date: 2006-01-20
forum: General Help
---

### Post by nrwilk on 2006-01-20
There are several really nice software tools for the mac that I use to use to duplicate partitions on seperate drives, and I'm wondering if anyone can suggest a good one for Kubuntu.  What I need to do is this:

* Duplicate a partition to my firewire harddrive
* Boot from the duplicated partition on the firewire harddrive
* Duplicate the partition from the firewire harddrive back to the internal harddrive

The reason for this is that I was given this terrible advice to keep my XP partition big, and set aside a miniscule partition for Kubuntu.  Now I completely regret it, and I want to repartition so that I have more room in the Linux partition.

Also, I'll need to find a utility which I can use in XP to do the same thing for that partition.  If anyone has any advice about that, that'd be nice too.  I never have really used Windows, so I have no idea what kind of apps are out there for it.  (what the hell is a *registry*, anyway?)

---

### Post by ubuntuguru on 2006-01-20
use dd

---

### Post by morphodone on 2006-01-20
you can resize your xp partition...but of course the safest option is to back up all that data on another partition

just attach the firewire drive in xp and back up all the files you wouldn't want
to lose...like all of "my documents" etc...

then resize xp with a live linux cd or partition magic...
once that's done you can allocate that space to linux in a variety of ways.

you can use the free space for a /home partition
mount the space however you want - example /mnt/storage

or you could resize the linux partition of your choice...but you would want
to backup that data as well...

how are your linux paritions setup?

---

### Post by nrwilk on 2006-01-20
[QUOTE=morphodone]how are your linux paritions setup?[/QUOTE]

I have one 10 GB / partition and one 3 GB /home partition

I'd want to increase the size of both, I think.

The Windows partition is about 167 GB

---

### Post by morphodone on 2006-01-20
[QUOTE=Fealos]I have one 10 GB / partition and one 3 GB /home partition

I'd want to increase the size of both, I think.

The Windows partition is about 167 GB[/QUOTE]

alright, your /home parition -in general- should be larger than your
/ partition.   once your resize your xp partition you can move your /home partition.  

let's say you free up 30GB from xp...
1) you would make a parition on that free space
2) copy your data from /home to there
```
sudo mkdir /mnt/new
sudo mount -t auto /dev/hda"X" /mnt/new
cp -a /home/user /mnt/new
```
3) change your /etc/fstab to reflect this change
       just change the mounting point to /dev/hda"X"
4) reboot

---

### Post by nrwilk on 2006-01-20
[QUOTE=morphodone]alright, your /home parition -in general- should be larger than your
/ partition.[/QUOTE]

See, that's what I thought too.  But, I had other advice to make the partitions as I have them now.  I thought that was strange that the / partition should be bigger than /home.

---

### Post by bigken on 2006-03-14
You could download the linux rescue disc and use qt_parted to resize your partions if you go this way you must defrag the win xp partion 1st then boot from the rescue disc ive done this twice and had no probs 

[http://www.sysresccd.org/Main_Page ]("http://www.sysresccd.org/Main_Page")

---

