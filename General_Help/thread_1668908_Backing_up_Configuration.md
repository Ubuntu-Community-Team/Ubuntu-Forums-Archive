---
title: "Backing up Configuration"
date: 2011-01-16
forum: General Help
---

### Post by EnigmaticCoder on 2011-01-16
A challenging aspect of using Ubuntu is tweaking the configuration of programs and the system. Also challenging is backing up that configuration. I brainstormed what I would do to backup the configuration, but I'm looking for a more comprehensive guide.

Here's what I brainstormed in case you can think of anything to add:
- Back up home directory, including hidden directories (there may be problems with this)
- Find all services, ssh, apache, etcetera. Google for their config files
- To be extra thorough, look through installed packages for the ones most used or that should be backed up for security reasons.
- Backup mail
- Backup keyboard shortcuts
- Backup start up applications
- Backup grub config
- Backup display settings
- Backup compiz
- Backup Windows home folder
- Backup Desktop
- What else?

---

### Post by veggen on 2011-01-17
This has been asked a few times in the past already... and always remained without an answer...
So if you dare to try for yourself, be sure to post back the results.

---

### Post by mastablasta on 2011-01-17
i might be wrong but i think Mint backup tool handles configuration backing up as well as HOME folder backup. they developed it because they prefer to do fresh install upgrade.
 
also you could always clone the disk :-P

---

### Post by EnigmaticCoder on 2011-01-23
I looked into the mint backup tool, but it appeared to me that I would have to, essentially, install the mint distribution. However, I am not willing to do that. Might I be mislead about having to install the mint distribution?

I have been researching this problem more, trying to find other solutions. I discovered that most configuration files are located in /etc. So, I thought, "I'll just back up /etc and my /home directories." However, I logged onto the irc channel and asked, "Is it safe to use unison to synchronize the /etc directory? Or are some config files specific to a certain machine?" The reply: 
"many will be specific ; fatab for instance" So does this mean that if I tried to restore the config from my desktop to a new machine, that I'd experience problems?

Perhaps I should pick and choose directories from /etc to backup. How can I find the files I need to backup yet avoid backing up configurations that are specific to a certain computer?

Also, how can I synchronize the configurations between my desktop and laptop? (I already know how to synchronize my files and installed programs, but synchronizing configurations is a mystery to me.)

---

### Post by EnigmaticCoder on 2011-02-02
Bump

---

### Post by EnigmaticCoder on 2011-02-26
Bump

---

### Post by EnigmaticCoder on 2011-03-14
Last bump

---

### Post by xfacta on 2011-03-14
Simple Backup picks up all those by default, and also a list of installed apps and everything. Will backup to a disk or network target. I think it's one of the unsung heroes - I've used the backups to pull out long lost files or configs from an old /etc

The backups are accessible without special software too, so if you had to rebuild you can just pull out info you need to get started, then when everything's operational again, do some full-on restores.

sbackup and sbackup-gtk in the repositories

---

### Post by Perfect Storm on 2011-03-15
Have you taken a look at [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

It have backup tools.

---

### Post by HermanAB on 2011-03-15
Howdy,

If it is complicated, then you are doing it wrong...

You should backup /home and /etc.

---

