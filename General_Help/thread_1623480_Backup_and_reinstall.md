---
title: "Backup and reinstall?"
date: 2010-11-16
forum: General Help
---

### Post by adwhitenc on 2010-11-16
OK, so in about 10 days I will be installing windows 7 alongside ubuntu on my laptop. The problem is that I cannot install it anywhere but the first partition. 
Is there a way I can make a backup of my system that I can "install" once I install windows 7?

Also, I need to be able to store my OS in a smaller partition. 

Thank you in advance for your help.

---

### Post by 55tptag on 2010-11-16
Hi,

You can use Clonezilla to backup and restore partitions.  It's at [http://www.clonezilla.org/](http://www.clonezilla.org/)
You wrote "Also, I need to be able to store my OS in a smaller partition."  What OS are you referring to there?  If it's the Linux one you backup I'm sorry but I don't think Clonezilla lets you restore a partition to a smaller partition.

You can use Gparted to resize partitions.  It's at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

good luck!  and backup your data before beginning.

---

### Post by Verbeck on 2010-11-16
or you can use remastersys to make an installation disk (there's an option to include the the home folder too)

[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb)

---

### Post by adwhitenc on 2010-11-16
my partition settings are as follows:

1gb ext3 as /boot
20gb ext3 as /
135gb ext3 as /home
4gb swap

I have used 30gb of my home drive.
Could I use tar to make a backup of my home and use clonezilla to make a backup of my boot and root partitions. 

Better yet, could I make a startup disk of of my system and use tar to copy my home?

---

### Post by adwhitenc on 2010-11-30
Successful install of both 7 and ubuntu. Thanks for the help

---

### Post by 2011basket on 2010-11-30
Oh thans,i was looking for it too :)

---

