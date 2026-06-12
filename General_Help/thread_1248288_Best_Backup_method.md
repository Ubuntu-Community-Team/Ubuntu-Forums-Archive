---
title: "Best Backup method"
date: 2009-08-24
forum: General Help
---

### Post by daaussie on 2009-08-24
We have ubuntu workstations 9.04 which access files on a ubuntu 9.04 server.
To do backups i use a manual process:
I load a dual VISTA bootup - then use nero backup to backup/compress Server files onto the local machine, then upload the backup file to MOZY system.

But I need to do this regularly, which I don't mind to do on a weekly basis.

Now I want your ideas on how to do some overlapping backups just using UBUNTU.

For example, a daily backup on the server itself, done automatically at 9pm each night, with the 9pm backup being then copied across (on boot up) to another workstation (in case the server blows up, then we can use the data from the workstation).

If this is possible, i wouldn't have the slighest clue on the commands to use on ubuntu server or workstation.

I tried KEEP, but found it weird and out of date, plus it is no longer supported.

I look forward to your suggestions (and command template)

---

### Post by PGScooter on 2009-08-24
it seems you have two main tasks:
(1) writing a backup script
and
(2) getting it to run at the right times.

For (1) I would suggest rsync. It is very much supported and is extremely flexible and powerful. For info, check out the man page: ```
man rsync
```

For (2) There are some schedulers, but I would check out crontab and do it manually.

---

### Post by daaussie on 2009-08-25
Yes, that is right - 2 parts to it.
A backup, and to automate it.

Sounds like i will need to do a little research.

Thanks for your advice.

---

### Post by denver on 2009-08-25
You can also try  rdiff-backup (its in the repos). It does incremental backups of your data on per file bassis. So if you have 10000 files and only 2 have changed, only 2 files will be copied over. You may also recover past versions of the files from what ever increments you have saved.

---

### Post by sahabcse on 2009-08-25
Try Amanda backup server

for more info [http://ubuntulinux.co.in/Backup---Amanda-Setup-in-Ubuntu-7-10-with-Virtual-Tapes.php](http://ubuntulinux.co.in/Backup---Amanda-Setup-in-Ubuntu-7-10-with-Virtual-Tapes.php)

---

### Post by jimcooncat on 2009-08-25
I've been happy using rsnapshot for several years now. I run it on an Ubuntu box, and use it to pull from a Windows share on my "server".

Initial setup is a learning curve, but its well worth learning about. When you get done, you have a very simple-to-use directory of multiple backups. I haven't touched my configuration since I first set it up.

I don't see anything where MOZY is supported by anything you can install in Ubuntu. :-(

And you'd want rsnapshot to run on the machine where you'll store the data.

---

### Post by daaussie on 2009-09-04
Thanks for all your input. I am going to give rsnapshot a go. [http://rsnapshot.org/downloads.html](http://rsnapshot.org/downloads.html)

however with ubuntu, how do I install it exactly? 

PS jimcooncat I am going to: 
daily: install on 2 ubuntu workstations (in case one goes) to backup info off my ubuntu server
weekly: login to vista to upload that days backup to MOZY.
quarterly: cd burn

I don't believe in giving the server too many tasks to do, that's why servers break.... with workstations breaking it doesn't bring down everyone.

---

### Post by daaussie on 2009-09-04
under the ubuntu install files, i clicked to install the DEB file, but my system says: SAME VERSION IS AVAILABLE IN A SOFTWARE CHANNEL, you are recommended to install the software from the channel instead.

What does this mean?
How do I install from a channel?
Is that terminal? 
If so what is the command?

---

### Post by scouser73 on 2009-09-04
I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), it works like a charm.

---

### Post by daaussie on 2009-09-06
i tried pyback... and I found that it doesn't really compress the files... so what's the difference with just copying the files across?
does it do a verify of the copy?

---

### Post by jimcooncat on 2009-09-11
> **daaussie said:**
> however with ubuntu, how do I install it exactly? 
Sorry for not getting back to you on this.

Installation should be done using the package manager (synaptic or apt-get), not a download directly from the website -- until you get really good at linux.

Here are some excellent instructions. One change, though -- everywhere is says "vi", use "nano" instead. They're both good text editors, but it isn't obvious how to save and close with vi.
[http://http://www.cyberciti.biz/faq/linux-rsnapshot-backup-howto/]("http://http://www.cyberciti.biz/faq/linux-rsnapshot-backup-howto/")

---

