---
title: "In general what do you do when Ubuntu runs out of space?"
date: 2009-11-05
forum: General Help
---

### Post by Vostrocity on 2009-11-05
I run Ubuntu on a less-than-40GB partition, so there's almost no room to breathe. That 40GB is solely the OS and apps since I have all of my files on a separate partition. Well it's happened three times already where doing an update (not a version upgrade) has pushed my disk usage to 100%. At this point it seems to be too late to run to Synaptics and uninstall something as I don't have space to run anything anymore (warnings pop up telling me unable to copy/open things). By the time I reboot (in hopes of a miracle) I can't even log in past the GDM. The last times this happened I was forced to just Live CD gparted and extend my partition, but I don't want to have to do this every time. Right now I have to use Windows as Ubuntu is unusable.

---

### Post by falconindy on 2009-11-05
Uhhhh... Ubuntu shouldn't take up anywhere **close** to 40gb. Have you cleaned out your apt package cache lately?

```
sudo apt-get autoclean
sudo apt-get clean
```

---

### Post by alphacrucis2 on 2009-11-05
> **Vostrocity said:**
> I run Ubuntu on a less-than-40GB partition, so there's almost no room to breathe. That 40GB is solely the OS and apps since I have all of my files on a separate partition. Well it's happened three times already where doing an update (not a version upgrade) has pushed my disk usage to 100%. At this point it seems to be too late to run to Synaptics and uninstall something as I don't have space to run anything anymore (warnings pop up telling me unable to copy/open things). By the time I reboot (in hopes of a miracle) I can't even log in past the GDM. The last times this happened I was forced to just Live CD gparted and extend my partition, but I don't want to have to do this every time. Right now I have to use Windows as Ubuntu is unusable.

Seems rather excessive even with a lot of programs installed. I would have a look in the /var/log or /var/crash folders

---

### Post by Vostrocity on 2009-11-06
> **falconindy said:**
> Uhhhh... Ubuntu shouldn't take up anywhere **close** to 40gb. Have you cleaned out your apt package cache lately?

```
sudo apt-get autoclean
sudo apt-get clean
```
That got me an extra GB.

> **alphacrucis2 said:**
> Seems rather excessive even with a lot of programs installed. I would have a look in the /var/log or /var/crash folders
What am I supposed to look for?

---

### Post by XCan on 2009-11-06
> **Vostrocity said:**
> 
What am I supposed to look for?

Look if there are any in particular large files in there, or excessive amount of log files. Start by, for example, simply checking the sizes of the dirs.

---

### Post by louieb on 2009-11-06
[RecoverLostDiskSpace - Community Ubuntu Documentation ]("https://help.ubuntu.com/community/RecoverLostDiskSpace")or what to do when your disk gets full.

---

### Post by NFblaze on 2009-11-06
Use File Disk Analyzer ( also called baobob) and use it to find out where most of the space concentration is and see if I can downsize anything.

---

### Post by Shpongle on 2009-11-06
maybe get an external hdd i got a 1tb for 90 euro!! , i keep all my files and backups on that!!

---

### Post by Vostrocity on 2009-11-06
> **XCan said:**
> Look if there are any in particular large files in there, or excessive amount of log files. Start by, for example, simply checking the sizes of the dirs.
Nah, only 27MB in the 'log' folder and nothing in 'crash'.

> **louieb said:**
> [RecoverLostDiskSpace - Community Ubuntu Documentation ]("https://help.ubuntu.com/community/RecoverLostDiskSpace")or what to do when your disk gets full.
That was a good learning experience, but only freed up a couple MBs.

[B]> **NFblaze said:**
> Use File Disk Analyzer ( also called baobob) and use it to find out where most of the space concentration is and see if I can downsize anything.
Now here's where it gets interesting. Look at my attached image, it shows 47.3 GB used  of 81.7 GB. However under that it shows only 21.4 GB of data all added together, which seems about right by my usage. FYI I did a filesystem scan which includes my Files partition shown as sda5 as well as my Ubuntu boot partition. So where is that extra 20 some GBs coming from?[/B]
[IMG]http://i33.tinypic.com/2dihspk.png[/IMG]

> **DillByrne said:**
> maybe get an external hdd i got a 1tb for 90 euro!! , i keep all my files and backups on that!!
Not very practical for me.

---

### Post by louieb on 2009-11-06
the chart says you have 34+ GB free - wonder where its at.  
What does 
```
df -h
``` show

---

### Post by Vostrocity on 2009-11-06
> **louieb said:**
> the chart says you have 34+ GB free - wonder where its at.  
What does 
```
df -h
``` show

Well that scan included both of my partitions. My Ubuntu partition is now 36.5 GB out of 47.5 GB (81%) while my Files partition 10.7 GB out of 34.2 GB (31%) so most of that extra space is from my 
Files partition. I'd also just finished extending an extra 10GB onto my Ubuntu partition with gparted. What I am wondering is why there's the inconsistency between the two sum used amount size.

---

### Post by monkeyKata on 2009-11-06
I have nothing to add to your question, but just wanted to ask what font and icon set you were using in that screenshot.  Thinking the icons might be Simple.  It looks nice.

---

### Post by louieb on 2009-11-06
> **Vostrocity said:**
> ... My Ubuntu partition is now 36.5 GB out of 47.5 GB 

36 GB is about 10 times what it should be. Are you using sbackup?   Should be obvious what the big disk users are.
did you try 
```
sudo du -h --max-depth=1 / | grep '[0-9]G\>'
```

like the guide I linked earlier. should only list /usr ,/media and /  - anything else is a problem.


> What I am wondering is why there's the inconsistency between the two sum used amount size. 	

Reserved space (5%), journal space - depends on where you look may show up as use or free or doesn't show up at all. Sure theirs a detailed  explanation somewhere.  I just take the numbers as being within 5% or so of being right.  Don't think I've ever seen things add up to 100% or having two ways of showing used and free space agree.

---

### Post by Vostrocity on 2009-11-06
> **monkeyKata said:**
> I have nothing to add to your question, but just wanted to ask what font and icon set you were using in that screenshot.  Thinking the icons might be Simple.  It looks nice.
Thank you. You're right the icon theme is Simple. And it's Glow Metacity Dark with Glossy controls. The font is Droid (Android's default font), [install here]("http://www.omgubuntu.co.uk/2009/08/quickly-install-google-android-fonts.html").

> **louieb said:**
> 36 GB is about 10 times what it should be. Are you using sbackup?   Should be obvious what the big disk users are.
did you try 
```
sudo du -h --max-depth=1 / | grep '[0-9]G\>'
```

like the guide I linked earlier. should only list /usr ,/media and /  - anything else is a problem.




Reserved space (5%), journal space - depends on where you look may show up as use or free or doesn't show up at all. Sure theirs a detailed  explanation somewhere.  I just take the numbers as being within 5% or so of being right.  Don't think I've ever seen things add up to 100% or having two ways of showing used and free space agree.
> 37G	/media
4.6G	/usr
du: cannot access `/proc/11107/task/11107/fd/4': No such file or directory
du: cannot access `/proc/11107/task/11107/fdinfo/4': No such file or directory
du: cannot access `/proc/11107/fd/4': No such file or directory
du: cannot access `/proc/11107/fdinfo/4': No such file or directory
du: cannot access `/home/andrew/.gvfs': Permission denied
5.4G	/home
47G	/

This is what I got, which doesn't seem very useful. You did remind me that Simple Backup could be the culprit, as the guide you linked to also said. I have it set for weekly backup onto a USB HDD that's not always connected. And checking the settings right now I was amazed that the "Abort backup if destination directory does not exist" checkbox wasn't checked! So now I have suspicions on that but I didn't find any thing when I tried the search prompt that was on the guide.

---

### Post by louieb on 2009-11-06
Actually those numbers look a lot better. the 47GB showing for / include the 37GB in /media and 5+GB in /home. I guess /home is in a separate partition.  

That means / has 5- 10GB in it. only about 1.2x or 2x to high.  a few stray backups could account for that. Still would like to see the **df -h** output.

---

### Post by Vostrocity on 2009-11-07
Oh sorry forgot to do that the first time you asked.

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              48G   37G  8.6G  82% /
udev                 1007M  272K 1006M   1% /dev
none                 1007M  2.2M 1004M   1% /dev/shm
none                 1007M  208K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda5              35G   11G   24G  32% /media/sda5


---

### Post by louieb on 2009-11-07
About out of ideas. Subtracting the /home folder - your / (root) partition should not use more that 5-10GB. Kind of hard to hide 27+GB
Did you check trash folders
```
sudo find / -type d -name '*Trash*' | sudo xargs du -h 
```Another hiding place is lost +found 
```
sudo find / -name ''lost+found'' | sudo xargs du -h
```

---

### Post by Vostrocity on 2009-11-07
Since I realized that my sbackup script wasn't setup properly, I did this search and found this.
```
andrew@Vostrocity:~$ sudo find / -name '*' -size +1G
/media/LaCie Backup/2009-10-29_00.32.15.130210.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-09-10_15.36.10.480066.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-06-14_11.08.51.728769.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-07-30_21.03.21.154575.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-11-05_16.15.55.409989.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-10-22_15.35.23.256913.Vostrocity.ful/files.tgz

```
I'm pretty certain these are what's causing the disk usage problem. I need to know how to delete them. I can't open the folder from the GUI since it says I don't have permission.

---

### Post by heiNey on 2009-11-07
> **Vostrocity said:**
> Since I realized that my sbackup script wasn't setup properly, I did this search and found this.
```
andrew@Vostrocity:~$ sudo find / -name '*' -size +1G
/media/LaCie Backup/2009-10-29_00.32.15.130210.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-09-10_15.36.10.480066.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-06-14_11.08.51.728769.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-07-30_21.03.21.154575.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-11-05_16.15.55.409989.Vostrocity.ful/files.tgz
/media/LaCie Backup/2009-10-22_15.35.23.256913.Vostrocity.ful/files.tgz

```
I'm pretty certain these are what's causing the disk usage problem. I need to know how to delete them. I can't open the folder from the GUI since it says I don't have permission.

if you're certain those the files you want to delete, then do:

```

sudo rm -rf /media/LaCie*

```

that should work.  the -r means recursive and f means force

---

### Post by louieb on 2009-11-07
You can do it as heiNey suggested. 
or with the GUI 
```
gksudo nautilus
```If you use the GUI be sure to use keys <shift+delete>  

Delete alone will move the files to roots trash can and not free up disk space. 

:mrgreen:Glad it was some backup files and not some runaway log file.

---

### Post by Earl_Maroon on 2009-11-07
Shrink my Windows partition and extend my Ubuntu one.

---

### Post by Vostrocity on 2009-11-07
Thank you so much! As you can tell I'm no good at knowing which commands to use. Anyway I jumped from 8.6 GB free to 34.1 GB free. My Ubuntu partition is just 11 GB now. I've changed sbackup to only manual backups so I won't get this problem again. Thanks to everyone who helped me in this thread, especially louieb who gave me a ton of suggestions.
:D

Edit: @Earl_Maroon  Uh.. I didn't mean it that way, I was actually asking the question so people could help me.

---

