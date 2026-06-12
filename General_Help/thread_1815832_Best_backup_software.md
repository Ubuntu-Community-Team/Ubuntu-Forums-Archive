---
title: "Best backup software"
date: 2011-08-01
forum: General Help
---

### Post by cclloyd9785 on 2011-08-01
I saw a list of backup software on the help files, and was wondering what, in your opinions, is the best.

I think I might be doing full backups every so often, similar to that of Norton Ghost.  So if theres a program like that, that'd be great.  GUI is preffered but I can work with command line.

---

### Post by Foxheadz on 2011-08-01
I haven't used it much, but Deja Dup is pretty amazing and has a simple GUI and best of all its in the repositories!

---

### Post by Megaptera on 2011-08-01
I use Remastersys to create ISOs of my system and burn to DVD for backups, having transfered the ISO to an external drive. Quaint and perhaps old fashioned I know but it works for me!

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Rodney9 on 2011-08-01
I use [Clonezilla]("http://www.clonezilla.org/")

---

### Post by wildmanne39 on 2011-08-01
+1 for Deja Dup.

---

### Post by Chiel92 on 2011-08-01
I prefer this:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by ddastoor on 2011-08-01
If you want to backup all your software + instaleld programms, then, yes the above posted ones of clonezilla or remastersys or deja dup seem good. 

You could also try "aptonCD"
[[COLOR="Red"]https://launchpad.net/ubuntu/natty/+package/aptoncd[/COLOR]]("https://launchpad.net/ubuntu/natty/+package/aptoncd")

Another thing that I have begun to do (and I suspect a lot of people do) is to have a separate partion for /home, so every six months if and when you decide to go to the next version of Ubuntu, your data is "untouched" on that separate partition (you can set this up at installation time).

Ok so in the light of the above, if you want to ONLY backup your /home partition (whether on separate partition or not), "rsync" from the command line to an external HDD is a good option.

rsync's easier than I initially thought, in that, once you get all the options working, then just "remember" them going forward.

---

### Post by aeiah on 2011-08-01
clonezilla for the occasional full system image and daily incremental backups for the important stuff, using either plain old rsync or backintime

---

### Post by John-B on 2011-08-01
> **Chiel92 said:**
> I prefer this:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
So do I :)

---

### Post by Chiel92 on 2011-09-24
Today I'm content with the following. I create a backup by doing three steps. Note that I use dropbox to store the backup on a remote host.
[LIST=1]
[*]Copy all the stuff you want to backup to one directory. (In my case that's /home)
[*]Create an archive of that directory (use e.g. tar, gzip or both) and store it in a dropbox directory.
[*]Split your files into pieces with a decent size, e.g. 10 MB per piece. You can use the program 'split' for that. This is to make the uploading process smoother.
[/LIST]

In code:
Go to your home directory.
```

mkdir -p Dropbox/mybackup;
tar -cf Dropbox/mybackup/backup.tar /home;
split -b 10000000 Dropbox/mybackup/backup.tar
rm Dropbox/mybackup/backup.tar

dropbox start;

```

To recover, cat the split files, untar the archive, and restore everything you want.
Of course, you can put these things in a shell script.

I forgot to mention that I like to have a list with all installed packages along the backup. You can retrieve such a list and put it into a file with the following command:
```

dpkg --get-selections > packagelist

```

---

