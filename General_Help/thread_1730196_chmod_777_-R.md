---
title: "chmod 777 -R *"
date: 2011-04-15
forum: General Help
---

### Post by niiklas on 2011-04-15
I accidental ran this command on " / " and made my server useless cant even connect to network with it. I can access root from "safe mode" how can i restore my system to its former glory?

Any help is appreciated!

---

### Post by bodhi.zazen on 2011-04-15
Easiest method by far is to back up your data and re-install.

---

### Post by niiklas on 2011-04-15
> **bodhi.zazen said:**
> Easiest method by far is to back up your data and re-install.

I need to backup my MySQL databases how can I do that without an internet connection? If I cant recover the databases I am screwed big time. Since I haven't been taking backups....

---

### Post by WorMzy on 2011-04-15
[This may be of use to you]("http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive")

Back up your databases, your home folder, and /var/www (if you're hosting a website), then reinstall. Trying to fix a mistake like this will take hours, and there's no guarantee you'll ever really fix it. Reinstallation is definitely the way to go.

Just make sure you never do something like this again, and learn to keep backups. :)

---

### Post by bodhi.zazen on 2011-04-15
Most things in */?bin/* are going to have permissions of 755

You can try starting with that.

If that does not help, you will have to fire up a live CD or other system and start using find and other tools to start manually restoring your permissions, file by file, directory by directory, until it is fixed or you can pull your data.

mysql stores the database in /var/lib/mysql, copy (tar) that directory =)

---

### Post by niiklas on 2011-04-15
> **WorMzy said:**
> [This may be of use to you]("http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive")

Back up your databases, your home folder, and /var/www (if you're hosting a website), then reinstall. Trying to fix a mistake like this will take hours, and there's no guarantee you'll ever really fix it. Reinstallation is definitely the way to go.

Just make sure you never do something like this again, and learn to keep backups. :)

Thanks to both of you. Thing is I have a script running that was running that command each hour on a mounted HDD. Today I upgraded my hardware with a new motherboard, CPU&memory and the SATA ports was changed. So instead of running the command on the secondary HDD it ran on the system HDD. Sucks to be me.. but lesson learned wont fall for this again!

---

### Post by bodhi.zazen on 2011-04-15
Have you been able to recover your data ?

---

### Post by niiklas on 2011-04-16
> **bodhi.zazen said:**
> Have you been able to recover your data ?


Yepp, chmodded some directories so that I was able to run the  MySQL server.  Still looking for a empty dvd to burn ubuntu server on though... :)

---

### Post by LinuxDS on 2012-10-27
Hello!

I have the same task, i need to resque a MySQL database after "sudo chmod -R 777 /".
Which directories and their permissions need to fix (or chmoded)?

---

### Post by howefield on 2012-10-27
> **LinuxDS said:**
> I have the same task,

Then start a new thread.

You'll stand a better chance of getting help. Feel free to reference this thread if you feel it will help explain your issue.

Old Thread closed.

---

