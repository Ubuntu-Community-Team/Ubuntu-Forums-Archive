---
title: "not enough free disk space error..."
date: 2009-08-08
forum: General Help
---

### Post by evancipation on 2009-08-08
So,

I've just put Ubuntu for the first time, so I'm pretty sure this is an ignorant question, but I'd still love some help with it.

I'm running the upgrade manager to make it so I can install some bare essential programs (this is just my net computer, I've got another for music that will never touch the internet) and it's telling me I don't have enough free disk space on volume '/'.  Specifically, that the upgrades need 390m and I need to free up another 289m.

However, the disk usage analyzer says I've got about 20 gigs free.  What's the problem here?

---

### Post by mikewhatever on 2009-08-08
Can you post the output of **df -h** command from Applications->Accessories->Terminal to verify the sizes.

The update manager is a program that runs after you start the computer, but you can't install any new programs from there, no matter how bare or essential they are. It is for updates and upgrades only.

---

### Post by evancipation on 2009-08-08
Hi thanks for the quick response,

I should have clarified,  I'm just updating everything because things like Skype and Flash won't install without certain components (libnspr4-dev specifically), and someone on here said updating everything would probably fix it.  Regardless, here's the output:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.1G   94M  96% /
tmpfs                 248M     0  248M   0% /lib/init/rw
varrun                248M  112K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M  176K  248M   1% /dev
tmpfs                 248M  656K  248M   1% /dev/shm
lrm                   248M  2.4M  246M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1              34G   15G   20G  44% /media/Main Guy

---

### Post by merlinus on 2009-08-08
Useful info here:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by mikewhatever on 2009-08-08
As you can see, the root partition (sda6) is only 2.3gb, and it is 96% full. You should enlarge is to about 10 gb, and since you've only just installed, I'd suggest reinstalling, and repartitioning in the process.

---

### Post by drs305 on 2009-08-08
> **mikewhatever said:**
> As you can see, the root partition (sda6) is only 2.3gb, and it is 96% full. You should enlarge is to about 10 gb, and since you've only just installed, I'd suggest reinstalling, and repartitioning in the process.

The link provided by merlinus will tell you how to resize the / system partition. If you prefer to reinstall, as suggested by mikewhatever, there is a companion link on why the install ended up with only 2.3GB and how to prevent that from happening on the next install. Here is the second link:
[http://ubuntuforums.org/showthread.php?p=7658271#post7658271]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")
Be sure to click on the jpg link which shows what you must to in the Partitioning (Step 4) process to expand the / partition.

---

