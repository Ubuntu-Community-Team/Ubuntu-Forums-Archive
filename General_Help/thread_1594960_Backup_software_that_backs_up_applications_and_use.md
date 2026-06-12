---
title: "Backup software that backs up applications and user data"
date: 2010-10-12
forum: General Help
---

### Post by Cavin on 2010-10-12
Hello,

I have searched and searched for answers to this question, but I can't find what I'm searching for anywhere. At least with the search terms I'm using.

So, my question is, is there a **backup software for Linux** that backs up **not only a user's home folder, etc, but also the user's applications, and its associated data**. 

I am about to upgrade my mother's computer to Lucid, but I don't want to do that until I can find a backup solution that will ensure she doesn't lose any of her application data. She has a lot of apps on her netbook, so just finding out where each individual app stores its data and backing it up is kind of out of the question. Unless every app that the end-user uses (that isn't run as root, obviously) stores its data in the home folder, then it would be easier.

Honestly, I use a Mac and I guess I'm just used to the simplicity of Time Machine, which certainly backs up applications, application data, user data, and even extra executables in all the /bin folders (which Macs don't typically use to store most applications). I've heard TimeVault is like Time Machine, but when I tried to use it on her computer, it wouldn't work because it wasn't compatible with the version of Ubuntu that was (and still is) on her computer.

Okay so anyone have any suggestions? :)

---

### Post by rewyllys on 2010-10-12
> **Cavin said:**
> Hello,

I have searched and searched for answers to this question, but I can't find what I'm searching for anywhere. At least with the search terms I'm using.

So, my question is, is there a backup  **software for Linux** that backs up **not only a user's home folder, etc, but also the user's applications, and its associated data**. 


I can recommend Lucky Backup.  It's available via the Synaptic Package Manager as "luckybackup", and its GUI is essentially self-explanatory.

---

### Post by Cavin on 2010-10-12
> **rewyllys said:**
> I can recommend Lucky Backup.  It's available via the Synaptic Package Manager as "luckybackup", and its GUI is essentially self-explanatory.
Thank you for your help, and Lucky Backup looks like an excellent tool. However, like other backup solutions, it requires the user to pick which directories to backup. While this is useful for backing up the data in a user's home folder, it doesn't solve the problem of backing up the user's application data. That is, unless application data **is** stored in the home folder, in which case all I'd have to do is get a list of installed applications (probably easy to do through dpkg), install them, and then restore the user's home data.
I haven't actually tried this, because I haven't wanted to risk having losing anything to begin with and also I haven't had much free time to do things like this on my Ubuntu partition on my laptop.

---

### Post by rewyllys on 2010-10-17
> **Cavin said:**
> Thank you for your help, and Lucky Backup looks like an excellent tool. However, like other backup solutions, it requires the user to pick which directories to backup. While this is useful for backing up the data in a user's home folder, it doesn't solve the problem of backing up the user's application data. That is, unless application data **is** stored in the home folder, in which case all I'd have to do is get a list of installed applications (probably easy to do through dpkg), install them, and then restore the user's home data.
I haven't actually tried this, because I haven't wanted to risk having losing anything to begin with and also I haven't had much free time to do things like this on my Ubuntu partition on my laptop.
Yes, in Ubuntu (and Linux in general) the "application data **is** stored in the home folder".  So also are the user's configuration files and profiles for each application.  
The result is, as you said, "all [you'd] have to do is get a list of installed applications . . . ."
It's especially easy if you have the root folder, "/", and the home folder, "/home", installed on separate partitions.  I do, and I just finished a clean install of Maverick by reformatting the partition that had contained the root folder "/" for Lucid, and then installing Maverick on that same partition.  Then all I had to do was re-install a half-dozen or so applications that were not installed as part of the Maverick installation, and they immediately resumed running, taking off from where they had been left the last time I closed Lucid.
BTW, I keep a list of those half-dozen or so applications, to aid my often feeble memory.:)
Good luck to you!

---

### Post by Cavin on 2010-10-17
> **rewyllys said:**
> Yes, in Ubuntu (and Linux in general) the "application data **is** stored in the home folder".  So also are the user's configuration files and profiles for each application.  
The result is, as you said, "all [you'd] have to do is get a list of installed applications . . . ."
It's especially easy if you have the root folder, "/", and the home folder, "/home", installed on separate partitions.  I do, and I just finished a clean install of Maverick by reformatting the partition that had contained the root folder "/" for Lucid, and then installing Maverick on that same partition.  Then all I had to do was re-install a half-dozen or so applications that were not installed as part of the Maverick installation, and they immediately resumed running, taking off from where they had been left the last time I closed Lucid.
BTW, I keep a list of those half-dozen or so applications, to aid my often feeble memory.:)
Good luck to you!
Awesome! Thank you!
I used sbackup after I asked this question. I used it because on Ubuntu's documentation lists it as the official backup software. Anyway, I backed up /etc /var /home/leslie  and /usr/local. I guess when/if I restore, I'll just use /home/leslie then. :) Thank you!

---

### Post by rewyllys on 2010-10-18
> **Cavin said:**
> Awesome! Thank you!
I used sbackup after I asked this question. I used it because on Ubuntu's documentation it lists it as the official backup software. Anyway, I backed up /etc /var /home/leslie  and /usr/local. I guess when/if I restore, I'll just use /home/leslie then. :) Thank you!
sbackup will do the job, but I think you have to initiate each backup when you use it.  To me, the attraction of Lucky Backup is that it makes it easy to schedule backups.  Using LB, I run a scheduled backup of my desktop's home folder, to an external hard drive, every night at 0100.  
After the initial backup, LB modifies only those files on the external hard drive that correspond to the relatively few files on the /home folder that have changed within the preceding 24 hours; and this takes only a few minutes.

---

### Post by Cavin on 2010-10-19
Well that isn't quite true. You can actually do schedules and stuff. However, I still should have listen to you to begin with because sbackup likes to make corrupt tgz files. I found this out after I re-installed Ubuntu 10.04 because 10.10 is slow on this computer. So, I lost everything. Luckily, my mom didn't have anything important on this computer. But that is beside the point really. I would much rather use a backup that, in the case she did have something important, she'd have it backed up. I'll give Lucky a try.

---

