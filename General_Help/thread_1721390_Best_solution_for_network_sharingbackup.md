---
title: "Best solution for network sharing/backup?"
date: 2011-04-04
forum: General Help
---

### Post by mydoghasworms on 2011-04-04
I have a home network linked to a DSL router and IP over power, so I'm basically only using my home computer and my laptop on it. My router allows me to plug in a USB drive and share it over the network via FTP.

What is the best solution for backing up or sharing documents between my two computers? I would like something that could automatically synchronize the contents of e.g. ~/Documents on each computer to the USB drive.

What would you recommend?

---

### Post by seawolf167 on 2011-04-05
Take a look at *rsync*

```
man rsync
```

An example command to mirror a directory from /computer1 to /extdrive is

```
rsync -ruv --delete /computer1/path /extdrive/path
```

As for sharing files, use *samba* (you'll definitely need samba if any other computer is Windows-based).

---

### Post by Zanthir on 2011-04-05
That command works on a Linux machine. How about if I want to back up from a Windows machine to a Linux machine?
 
Last night I set up a Samba file share server, and just drag and dropped the files into the new shared folder. I'm worried that next time I go to back up I'll have difficulties sorting out what is new and what is already backed up? Could have I used rsync to do this, or is there a better way to do this in general?
 
Also, I need to free up space on this laptop I was backing up, so I may need to delete some of these files, but I'd like to keep them on the backup, so should I be syncing, or again, is there a better way?

---

### Post by mydoghasworms on 2011-04-05
Thanks guys for the replies. However, I would like something that will automatically share/synchronize the contents of a specified folder. Something like Sparkleshare, I guess, but which I can set up to synchronize to the USB drive on the network.
By the way, my router allows sharing the USB drive as an SMB (Windows) share on the network as well.

---

### Post by mydoghasworms on 2011-04-05
Just to be clear: When I say automatically share/synchronize, I mean of course I don't want to have to copy the files myself.

---

### Post by seawolf167 on 2011-04-05
To both of the above posts - you can setup a crontab entry to automatically preform your tasks.

Click the crontab link in my sig for lost more info, but the basics are as follows:


[LIST=1]
[*]Create your command or bash script
[*]Run it to ensure it works and does what it wants you to
[*]Edit /etc/crontab and either add your command directly or add the path to your executable bash script
[*]Profit
[/LIST]
From Windows -> Ubuntu, I'd probably add an /etc/fstab entry for the Windows drive so it is automatically mounted, then you can use your linux commands on your linux box to sync files from your mounted Windows drive.

---

### Post by mydoghasworms on 2011-04-05
Thanks seawolf167, that sounds like a plan. I was hoping to find a GUI application to set it up, but I think this solution is probably the most sound and easy to implement, so I'm going to mark this thread as solved.
Thank you.

---

### Post by seawolf167 on 2011-04-05
Sbackup is a GUI front-end for rsync where you can tweak options and include/exclude what you want too. You can download it and see if you like it or not:

```
sudo apt-get install sbackup
```

You can probably use a network location provided it is mounted on your computer (where I'd add an /etc/fstab entry to ensure it can always be found).

---

