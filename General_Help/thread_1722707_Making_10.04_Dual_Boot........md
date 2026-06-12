---
title: "Making 10.04 Dual Boot......."
date: 2011-04-06
forum: General Help
---

### Post by old_dog on 2011-04-06
Morning Guys(well it is here!). I have been asked by a friend(He thinks I'm an expert....Fool) to make his 10.04 system dual boot i.e. have the option of using Windoze 7. I have tried to lead him away from the dark side....But he has a number of things that only run under "7". So can anyone point me in the right direction, what to use to partition the disk etc etc..
Any help appreciated.

---

### Post by 3Miro on 2011-04-06
First hit on Google:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

The most important thing: BACKUP EVERYTHING IMPORTANT FROM THE COMPUTER. Unless you know exactly what you are doing, messing up the partition is easy and can destroy all data on it.

On another note, have you considered Virtual Box, it is preferable to dual-boot as you can run windows from within Ubuntu. You cannot run games though as Virtual Box is not good when it comes to complicated graphics.

---

### Post by oldfred on 2011-04-06
+1 on 3Miro suggestions.

I recommend using windows tools for windows and Linux tools for Linux. 

So use Win7 to shrink its partition, but do not attemp to create new partitions with windows as it may convert from basic to dynamic and cause all sorts of issues. Then you can use gparted to create new partitions. But most systems with win7 seem to use all 4 primary partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first.
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

There is some confusion on auto install buttons that if clicked wrong will erase entire disk (use entire disk for Ubuntu.) Best to manually partition & use manual install.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

