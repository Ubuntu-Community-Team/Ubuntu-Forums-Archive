---
title: "File checks fail for /home partition"
date: 2010-02-28
forum: General Help
---

### Post by Joe Ker1086 on 2010-02-28
I have a dual boot with Arch linux that share a /home partition. Whenever ubuntu starts tho it tries to do a check on the /home partition and fails.... it gets an error saying unable to check then drops into a shell. I have to run it in recovery mode frequently then start it up and it usually works, but i have to type startx after logging into a shell before that.. any ideas?

---

### Post by tomski on 2010-02-28
it might be that arch uses different permissions on files which x needs at start 

has anything been reported in your log files? if so what?

---

### Post by Joe Ker1086 on 2010-02-28
Im not sure what the logs say yet....ill check the next time it happens on boot. anything in specific i should be looking for?

---

### Post by dcstar on 2010-02-28
> **tomski said:**
> it might be that arch uses different permissions on files which x needs at start 


Not just different permissions, sharing /home with a different OS is fraught with danger as each system will try to change configuration files and invariably make them incompatible with the other system.

Even using the same /home on two different Ubuntu versions will cause problems - primarily because of the different Gnome releases.

It is a really **bad** idea to share /home with different distros, share User folders under /home but not the user /home folder itself.

---

### Post by Joe Ker1086 on 2010-03-01
HMMM.....I was always told that it was a good idea to make a separate /home partition for the purpose of keeping all of your files in one place.... :(

---

### Post by Joe Ker1086 on 2010-03-01
what if i were to use different users on the same /home partition.... like lets say one user (me) uses arch and one user (user 2) uses ubuntu... if there are no common users between the distros will there still be a problem???

---

### Post by dabl on 2010-03-01
If you don't mind each user having his own separate data, that would work.  If you hope to share the data, then it won't work.

The better approach, to avoid garbled up settings in /home, will unfortunately require a complete rearrangement of your system.  Basically, you need to install /home with the root filesystem, all in a partition no larger than what you need for the OS and some growth space, and then you need a separate partition on which to save your user data. On the separate partition, you make directories, aka "folders", for "DOCS", "MUSIC", "PIX", whatever, and you will symlink them into the /home/user folder for each OS.  This way, you have one common set of your data, and each OS has a /home folder for you that has all the settings that you need for that OS, and the settings for each OS don't conflict with each other.

---

### Post by oldfred on 2010-03-01
More info on dabl's suggestion:

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partiti](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partiti)

oldfred's versions
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by philinux on 2010-03-01
As said above. 

I would say have a separate /home partition for each distro. Does not need to be very big but have a shared data partition.

---

