---
title: "Advice on TAR backup parameters"
date: 2009-11-23
forum: General Help
---

### Post by Manyette on 2009-11-23
Hi All, I'd appreciate some advice on backup of the entire system so that it could be reinstalled on a newly formatted drive if that became necessary. I am currently using the following parameters to the tar command and am eliminating directories which I believe I do not need on the backup, but would have to be recreated after a restore. Command executed from root as superuser.
---
tar -cvpzf /media/backup/karmic5.tar.gz --exclude=/media --exclude=/media/backup/karmic5.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/tmp /
---
Could someone knowledgeable on the needed files advise me if I'm eliminating to many directores, and any otheer things I might need to do for this purpose?  TIA

---

### Post by Manyette on 2009-11-26
Help please?  Surely someone is knowledgeable on the subject.  Please

---

### Post by NFblaze on 2009-11-26
As far as I know as a non-expert (I've only done about 3 tar backups this way), I'm unsure about the /sys directory, but it appears that everything else you have excluded is fine. Hopefully, this bump will get you more answers.

---

### Post by Manyette on 2009-11-26
Hi NFBlaze,and thank you.  Now that I look at it, you are absolutely right, and there is no "/sys" directory, and I'm not sure where I got that idea.  But obviously not the right one.  And if you feel the rest are correct, it gives me a bit more confidence.  It concerns me because an earlier backup turned out not to be a bootable restore.  (I've made some changes since, but it has left me gunshy!)  Anyway, thanks very much for your help.

Hmm!  Turns out I goofed again.  Interesting that the disk usage analyzer does not show the /sys directory, but I can use terminal to change to it, and then discover that there are indeed some necessary files there. But I wouldn't have looked if you hadn't prompted me to, so thanks again!

---

### Post by NFblaze on 2009-11-26
When you say bootable restore, was it because of grub or partitioning? As in one of my previous restores I did I had to manually edit the grub file to reflect the new UUIDs and I used Testdisk to re-arrange which partitions where bootable. Tho, if you wont be editing anything that serious then it shouldnt be an issue.

---

### Post by Manyette on 2009-11-26
Well, I had not made any partition changes, and being definitely a newbie, the only info I can offer is that it booted to a terminal screen, stating that a file (unspecified) was missing.  I assume that I had failed to include something that was required.  It would have been helpful if it had added WHAT file was missing, but it didn't.  And that is what brought this subject up to begin with.  Understand, that I didn't lose anything, since I could restore /home and all the files therein, but I did have to do a fresh install of Karmic.  I'd really like to avoid having to do that again with a backup that I can trust.

---

### Post by blueridgedog on 2009-11-26
tar is not an ideal choice for system wide backups intended for bare metal recover.  Have a look at remastersys.

Lots of suggestions here:

[http://ohioloco.ubuntuforums.org/showthread.php?p=8275762](http://ohioloco.ubuntuforums.org/showthread.php?p=8275762)

---

### Post by louieb on 2009-11-26
There is a /sys directory - its a virtual one kind of like /proc. You can't write to it and no need to back it up.

Lots of good tar how tos in [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")

Heres the oldest and most referenced [Heliode: Backup and restore your system! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup")

Newer and a bit more technical [A-star: Backup and restore your system! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=81311&highlight=tar+backup")  
[Howto: Backup your PC using "tar" -  Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1019517&highlight=tar+backup") 

Normally do an image backup with partimage - partimage does not work with ext4 formated partitions. So i'm looking at  tar and fsachiver

---

### Post by Manyette on 2009-11-26
louieb & Blueridgedog, I thank both of you very much.  Feeling mellow and full of turkey, I will look over your suggestions.  My reasons for using tar are quite simply that I had used it some 30 years ago while working for Cyrix on a big Solaris system, and was at least slightly familiar with it. But as you can tell, I never had to do any admin tasks, and so am really very non knowledgeable about that side of *nix.  But I'm learning, slowly I'll admit.  Again, many thanks to you both for the links and suggestions.

---

