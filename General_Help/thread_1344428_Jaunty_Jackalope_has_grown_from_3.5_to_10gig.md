---
title: "Jaunty Jackalope has grown from 3.5 to 10gig"
date: 2009-12-02
forum: General Help
---

### Post by ozguitarplayer on 2009-12-02
Hi,
I have Jaunty Jackalope installed on one partition and have recently installed Karmic Koala on another partition on the same drive. In each case the partitions have the base operating systems only, all other files are on another partition. 

Jaunty Jackalope started taking up about 3.5 gig of it's partition. some where along the way it grew to be about 10 gig.
I don't have a large number of applications loaded into the operating system and on boot the grub screen shows only 1 listing of the kernel.

If there is more than 1 kernel could this be the problem even though it does not show in the grub screen? and if so is it possible to safely remove the extras?
Or is there another likely explanation as to why the size of the operating system would grow so much?

---

### Post by NFblaze on 2009-12-03
You can check to make sure that you deleted the kernel using Synaptic and making the "load-image"s are removed, that way they will remove them and the dependencies.

Have you typed in *sudo apt-get autoclean* and *sudo apt-get clean*

Also, try using File Disk Analayzer to see where all your disk space went.

---

### Post by steveneddy on 2009-12-03
> **NFblaze said:**
> You can check to make sure that you deleted the kernel using Synaptic and making the "load-image"s are removed, that way they will remove them and the dependencies.

Have you typed in *sudo apt-get autoclean* and *sudo apt-get clean*

Also, try using File Disk Analayzer to see where all your disk space went.

also

```
sudo apt-get autoremove
```

---

### Post by ozguitarplayer on 2009-12-03
thanks for those suggestions however they only removed a few Mb. I couldn't find File Disc Analyzer can you point me to it?

---

### Post by shaggy999 on 2009-12-03
Applications -> Accessories -> Disk Usage Analyzer

I am wondering if you have something that's spitting out runaway logs. They can grow to multi-gigs pretty quickly if an application is spitting out hundreds of errors/sec.

---

### Post by ozguitarplayer on 2009-12-03
> Applications -> Accessories -> Disk Usage Analyzer
Thanks, and there it was right in front of me and I did look in Accessories.
Why would an application be spitting out errors and how would I find such information?

---

### Post by jegerjensen on 2009-12-03
Most logs are plain text files in /var/log/

---

### Post by John Petley on 2009-12-03
I have the same problem in Karmic. var\log folder is 34.1GB and has filled the partition. My questions:
1) Is it safe to delete all of these?
2) How do I delete them? - I get this message "You are not the owner, so you can not change these permissions" and I cannot delete any of the files or folders that I have tried
3) How do Istop this problem happening again? It only started after I upgraded to Karmic.
 
Currently THe system is unusable so help would be very much appreciated

---

### Post by megamania on 2009-12-03
It could be this bug:
[http://ubuntuforums.org/showthread.php?t=1331883](http://ubuntuforums.org/showthread.php?t=1331883)

---

### Post by John Petley on 2009-12-03
Thanks. It looks like it but can you tell me (in very basic terms, please!) how to delete these log files and if it is unsafe to delete any of them?

---

### Post by zaphod777 on 2009-12-03
probably the easiest way would be to run

```
sudo nautilus
```

then navigate to that folder and delete the files.

your browser will be using root access.

you can use command line to do this but if you type the wrong thing you can remove much more than those files.

log files should be safe to delete but you could leave the last week or so just in case you need to troubleshoot an issue and need the logs.

---

### Post by jegerjensen on 2009-12-03
It should be safe to delete any files that end with .#.gz where # is a number.  The files with higher numbers are the oldest, so you may want to delete them first unless they are of insignificant size.

The files without .#.gz are still in use by the logging daemons, so by removing those you may interfere with some other process writing to the file simultaneously.  I don't know whether this can cause any trouble.

---

### Post by John Petley on 2009-12-03
Thanks very much I think I have my system back.

---

### Post by john newbuntu on 2009-12-03
There is a logrotate job that needs to be run by cron on a daily basis.  Please check the logs and see if it is getting run.  Otherwise fix that or for the time being, run the command:

```
sudo /usr/sbin/logrotate /etc/logrotate.conf
```

This will clear up some of the system logs.

---

