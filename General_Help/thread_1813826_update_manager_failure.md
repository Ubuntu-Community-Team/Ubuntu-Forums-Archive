---
title: "update manager failure"
date: 2011-07-28
forum: General Help
---

### Post by rootessa on 2011-07-28
HI and Thanks in advance!

Updated unbuntu and have been unable to use Update Manager since. Get message w/ big red button which reads:E Type 'ramberto/java/unbuntu' is not known on line2 in source list/etc/apt sources. list d/ferram roberto-java-maverick.list. I'm instructed to report this error.
Looking elsewhere online I'm told: check file permissions, 'etc/apt/sources.list' and also: 'sudo-apt-get update' as well as 'sudo-apt-get-install-f. These don't work and are not recognized. Any suggestions?

Thanks!

---

### Post by mendhak on 2011-07-28
Open up the Ubuntu Software Center, then 'Edit Software Sources'.  You'll need to look for the ramberto line in one of those tabs.  Delete it.

The other way is to make a backup of /etc/apt/sources.list, then open it in your favorite text editor.  Look for the ramberto lines and remove them. 

Then, sudo apt-get update.

---

### Post by rootessa on 2011-07-28
Thanks!
I can't open the Software Center. I click on the icon, it begins to initialize but does not open. This system has many, many problems and I'm ready to heave it out the window.

---

### Post by rootessa on 2011-07-28
trying it the other way I get Bash:/etc/apt/sources.list:Permission denied

---

### Post by plucky on 2011-07-28
> E Type 'ramberto/java/unbuntu' is not known on line2 in source list/etc/apt sources. list d/ferram roberto-java-maverick.list.

Open a terminal and post output of ```
ls -l /etc/apt/sources.list.d/
```

You are looking for the file "ferram-roberto-java-maverick.list" and what it contains.

---

### Post by rootessa on 2011-07-31
-rw-r--r-- 1 root root  66 2011-03-22 23:54 ferramroberto-java-lucid.list.distUpgrade
-rw-r--r-- 1 root root 105 2011-03-23 11:43 ferramroberto-java-lucid.list.save
-rw-r--r-- 1 root root 142 2011-03-27 10:17 ferramroberto-java-maverick.list
-rw-r--r-- 1 root root 142 2011-03-27 10:17 ferramroberto-java-maverick.list.save

OK.Found them. Do I delete them all? 
Thanks!

---

### Post by plucky on 2011-07-31
> **rootessa said:**
> -rw-r--r-- 1 root root  66 2011-03-22 23:54 ferramroberto-java-lucid.list.distUpgrade
-rw-r--r-- 1 root root 105 2011-03-23 11:43 ferramroberto-java-lucid.list.save
-rw-r--r-- 1 root root 142 2011-03-27 10:17 ferramroberto-java-maverick.list
-rw-r--r-- 1 root root 142 2011-03-27 10:17 ferramroberto-java-maverick.list.save

OK.Found them. Do I delete them all? 
Thanks!

Try ```
cat /etc/apt/sources.list.d/ferramroberto-java-maverick.list
``` and post output.

Do you need that PPA?


If not,then you can delete the files.

Good Luck

---

### Post by rootessa on 2011-07-31
Thanks!
I get:

user@user-laptop:~$ cat /etc/apt/sources.list.d/ferramroberto-java-maverick.list# deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) maverick main # disabled on upgrade to maverick
ramroberto/java/ubuntu maverick main

no, I don't need the PPA. Was just sitting here wondering if I should just uninstall and re-install Linux. This whole system is messed up. Maybe it's just one problem at a time. I also don't know (yet) how to delete this stuff..........I'm such a moron! :tongue:

Thanks again!

---

### Post by plucky on 2011-07-31
> **rootessa said:**
> Thanks!
I get:

user@user-laptop:~$ cat /etc/apt/sources.list.d/ferramroberto-java-maverick.list# deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) maverick main # disabled on upgrade to maverick
ramroberto/java/ubuntu maverick main

no, I don't need the PPA. Was just sitting here wondering if I should just uninstall and re-install Linux. This whole system is messed up. Maybe it's just one problem at a time. I also don't know (yet) how to delete this stuff..........I'm such a moron! :tongue:

Thanks again!

From a terminal ```
sudo rm /etc/apt/sources.list.d/ferramroberto-java-maverick.*
```

Or

Open Software Sources and delete the PPA there.

Good Luck

---

### Post by rootessa on 2011-07-31
Happy Dance! OH Happy Dance! It's updating itself! I can open the Software Center and Update Manager is running! Thank-you SO much! I'm a very Happy Camper!  \\:D/ kate

---

