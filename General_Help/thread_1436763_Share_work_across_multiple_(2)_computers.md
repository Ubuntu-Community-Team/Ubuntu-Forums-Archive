---
title: "Share work across multiple (2) computers"
date: 2010-03-23
forum: General Help
---

### Post by dagomar on 2010-03-23
I've been looking for a solution to a wish I have. I am a webdeveloper and I have 2 computers (laptop + desktop) that I use for work. Both run Ubuntu 9.10. What I would like is that my server set-up is automatically being mirrored between these 2 computers, so I always have the latest version of my work with me. I've been looking at version control (bazaar), but I am not sure that this is what I mean, and I dont know if it will work with mysql. I imagined it should be something like 'ubuntu one', but then only across 2 computers. There are 2 folders that should be mirrored; /var/www and /var/lib/mysql. and when I say mirrored I mean everything, including file permissions. The software should check which is newer and preferably make backups eligible for restoration in case something goes wrong. 

I have been looking but could not find anything in particular. I am hoping there is someone out there who has a similar use-scenario and would be willing to share insights. thanks.

---

### Post by leg on 2010-03-23
Well all I have done is leave my desktop machine on as a server and set up ssh on it. Now I can access everything in /var/www by logging on to it through gftp. I don't use the machine as a desktop anymore though so it may not suit you.

---

### Post by thebigob on 2010-03-23
I would look into subversion

This is a great way of maintaining files on various machines.

Once set up this would provide exactly the solution you are looking for.

---

### Post by dagomar on 2010-03-23
Thanks both!

Indeed I think subversion is the most logical solution. Does this also work for mysql though? I understood that may be a bit difficult to accomplish, also, it may not be exactly what subversion is intended for, hence my question.

---

### Post by john newbuntu on 2010-03-23
Since you are looking at accessing the same files between just 2 computers, would'nt it be simple to set up a network share across the 2 machines? (plus the routine backup of that folder).  ssh is something as leg pointed out or you might want to look into a NAS like solution.  Pardon me if I am missing something here.
But subversion, cvs or any other form of SCM is primarily for version control (i.e., maintain incremental changes to source code etc with several developers working on it)  It would still require a repository on one of the machine to store data. Although it might serve your purpose, it seems to me like the wrong tool.
If you want a syncing option between the two boxes, try rsync.

---

### Post by mwaschkowski on 2010-06-08
You could also try dropbox, it supports Windows, Linux and Mac, and it just a breeze to setup and use. Subversion will give you a version history, which dropbox won't, but dropbox is even simpler and so I use Subversion for my code but dropbox for my 'regular' documents and data. And its free for the first 2GB

If you signup through the following we both get an extra 250MB of storage:

  [https://www.dropbox.com/referrals/NTcwMTg5MzE5](https://www.dropbox.com/referrals/NTcwMTg5MzE5)

Cheers,

Mark

---

### Post by bodhi.zazen on 2010-06-08
I advise you either :

1. Use a network share (On a LAN I would use NFS).

2. Take a look at rsync

[http://lifehacker.com/196122/geek-to-live--mirror-files-across-systems-with-rsync](http://lifehacker.com/196122/geek-to-live--mirror-files-across-systems-with-rsync)

[http://www.linuxquestions.org/linux/answers/Networking/Using_rsync_to_mirror_data_between_servers](http://www.linuxquestions.org/linux/answers/Networking/Using_rsync_to_mirror_data_between_servers)

subversion would work if you want the additional features of revision control.

---

### Post by luceerose on 2010-06-08
> **leg said:**
> Well all I have done is leave my desktop machine on as a server and set up ssh on it. Now I can access everything in /var/www by logging on to it through gftp. I don't use the machine as a desktop anymore though so it may not suit you.

I do the same.
I still have a copy of my files on all my other computers just for backup.
Anytime I want to work with or modify my files I either sit on the main computer or ssh it from one of the other computers. So only one hard drive that's up-to-date really. I do frequent backups to the main computers 2nd hard drive &, when I feel like it, all the other computers drives & an external hard drive.

---

