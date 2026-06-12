---
title: "Suggestions for a *Good* OS backup program?"
date: 2010-07-16
forum: General Help
---

### Post by jimjenia on 2010-07-16
Ok, Noobe to Ubuntu, recently installed Lucid, did all the updates, Got my UT 99 loaded and working natively with TeamSpeak 3 (yea, even the sound works now) ... I really like the setup I have now.

Question?

Can some one recommend a good backup program to use that will "completely" backup my current system "as installed"?

I have installed "Back in Time", and it seems really easy to use, but I'm looking for something similar to (sorry have to say it "Windows System Restore").

I've tweaked and tweaked, updated my ALSA drivers, working openAL and got the latest ATI driver installed for my ATI 5770 ... even got a Xfi linux beta working from Creative (that was fun) ..

Any recommendations would be greatly appreciated. Something user friendly too, I'm learning, but still very new to Linux/commandline/Ubuntu.

Thanks!

~Jim~

---

### Post by techunit on 2010-07-16
Hi welcome the wonderful world of Ubuntu!... Generally in order to preserve as much as there OS as possible expierenced users create partitions manually during the install and give Ubuntu a so called Home Partition. Thus when they reinstall they don't have to start from scratch. But because of the nature of most harddrives today this poses a problem if you are dual booting... The best thing you can do is back-up you home folder... to do this make sure you have a removable media that is large enough to contain your files. [Here is a video covering backing up your home folder]("http://ubuntuvideotutorials.wordpress.com/2010/06/28/back-up-your-data-in-ubuntu/"). You need to back it up to a removable medium otherwise you are going to get stuck in a loop...

for what you want to back-up ```
/home/yourusername
```Then when you restore it your settings will be there for when you reinstall your applications.

I hope this helps...

---

### Post by jimjenia on 2010-07-16
Thanks for the reply!

I have backed up my home folder to a USB 1 T Drive, using Back-in-time.

I just didn't know if that actually copied all the hidden files, bin's, lib's, etc.

I tried backing up the root dir with Back-in-Time, but even though it has a 'root' user function, it didn't appear to copy everything, just my home folder.

Is that enough, my main concern is all the drivers, libs, etc that I "finally" got right to make the sound in games/TeamSpeak/video's/etc all work ...

But if backing up the home folder is all I need then cool, guess I'll just stick with a scheduled Back-in-time.

thanks!

Jim

---

### Post by oldfred on 2010-07-16
If you have installed a lot of applications it is worth while to make a list of them. I do this before each backup of /home so I also have a current list of installed apps. I also try to make copies of any file in /etc that I manually edit to I have copies of that customization in /home.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by Megaptera on 2010-07-16
Hi Jim,
You might like to look at Remastersys. I create backup DVDs of my whole system just in case. Infact used one to reinstall 10.04 today after I messed up! All up & running as I wanted it in about 30 mins:

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Hope this helps?
Richard

---

### Post by betlog on 2010-07-16
clonezilla is a good sector-by-sector tool.. kinda like old norton ghost.. boot from a cd and text interface
puppylinux has a similar app (and the always helpful puppylinux tips to guide you)

or then there is apps that just copy/restor individual files/folders:
 rsync and the gui for it; grsync
or what i am tesitng currently; sbackup

---

### Post by mike555 on 2010-07-16
You might want to try "RedoBackup.org "

---

### Post by jimjenia on 2010-07-16
Thanks to all for the replies!

Looks like I have some more reading to do. I like the clonzilla idea and am heading now to check out remastersys .... both look promising for what I need.

Thanks again!

~Jim~

---

### Post by Megaptera on 2010-07-17
You're welcome!

---

### Post by supermorph on 2011-03-25
mega suggested a good tool,
my brother suggested clonezilla above, (havent tried that yet)

but providing your home folder isnt huge, you could use remastersys

you can even make a custom dvd this way.
it has the ability to backup your entire ubuntu install
within just under dvd5 limits (as far as i am currently aware)

i did this for 9.04 development edition 
(i made a custom dvd pre-configured and customised e.g logos, software)

hope this is helpful

kind regards
supermorph

---

### Post by sammiev on 2011-03-25
+1 for clonezilla as I love to play with many OS and can always put it back to what it was. Including Windows if you use a dual boot system. GL :)

---

### Post by rgb1701 on 2011-03-25
Yes, Clonezilla is the "right way" to backup an OS (/) partition-

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by elewis on 2011-05-04
sbackup has been an excellent and very reliable utility I used on 8.04 and am using on several 10.04 work stations. Unfortunately, sbackup does not currently work on 11.04 for any file restoration. Having a reliable backup program is sufficiently important that I had to roll back an 11.04 installation to 10.04 in order to have sbackup.

---

### Post by jerenept on 2011-05-04
I use BackInTime (no compression) and Deja-Dup (compression, and encryption if you want) depending on the circumstances; I prefer deja-dup though.

[Install Backintime in Ubuntu]("apt://backintime-gtk")
[in KUbuntu]("apt://backintime-kde")
[Install Deja-Dup]("apt://deja-dup")

---

### Post by sammiev on 2011-05-04
clonezilla boots on its own cd/dvd and is great for backing up all OS and partitions. Try them all and choose the one that works best for you. GL :)

---

