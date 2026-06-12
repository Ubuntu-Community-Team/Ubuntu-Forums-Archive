---
title: "Could someone help me set up backups of my system"
date: 2006-02-16
forum: General Help
---

### Post by GreatestGravity on 2006-02-16
So, I've been trying to set up daily system backups to an external hard drive. (FAT32)

I've tried a couple of different backup programs, and they haven't worked, for various reasons - or maybe I just haven't been able to configure them right :(  

The closest to working was backup2l, which made backups right - but I couldn't get the incremental backups to work nicely, every other one seemed to take up as much space as my entire system. 

A couple ran into trouble with the file size limit of the filesystem, or so it seemed...



...could someone help me? Either point me to some step-by-step instructions or just post how to do it... I've tried myself and it just got really frustrating, since I don't know whether things don't work because I've misconfigured it or because I'm picking the wrong tool for the job.

---

### Post by GreatestGravity on 2006-02-17
Anyone? This is hopefully not too rare of a thing to be doing...

---

### Post by disabled_20220313 on 2006-02-17
Hi,

Try this, bit of a hardcore way of doing it.

[http://www.ubuntuforums.org/showthread.php?t=81311&highlight=backup](http://www.ubuntuforums.org/showthread.php?t=81311&highlight=backup)

The "Customisation Tips and Tricks" sub-forum is a good place to search for this kind of thing.

Ciaran

---

### Post by steevc on 2006-02-17
I just did a [write-up]("http://www.bagofspoons.net/cgi-bin/pyblosxom.cgi/Computer/20060214backup.html") on my experiences with backup. I've settled on [rdiff-backup]("http://www.nongnu.org/rdiff-backup/") as it does what I want. I'm using it to backup to a remote server, but it should work with an external drive too.

---

