---
title: "Ubuntu upgrade to 11.04 failed"
date: 2011-07-06
forum: General Help
---

### Post by krbhnp on 2011-07-06
Hi i am currently running ubuntu 10.10 and want to upgrade to 11.04 but as i click on the check  for updates button on the update manager, it displays the message as follows:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.


If i directly click on the Update button on the update manager to upgrade to 11.04, it just remains idle for sometime and does nothing...i am a new user...Please help me...
Thanks in advance...

---

### Post by seawolf167 on 2011-07-06
I'm not sure about the error - but regardless, I suggest doing a fresh install changing to Unity from Gnome.

Make a backup with [Clonezilla ]("http://www.clonezilla.org")just in case, then IMO the best thing to do would be to move /home to its own [separate partition ]("https://help.ubuntu.com/community/Partitioning/Home/Moving")then just reinstall / (root) with an install cd and all your settings, documents, files, etc. will still be there (on /home).

---

### Post by Rubi1200 on 2011-07-06
You can try the following commands in the terminal and see if it helps resolve the issue:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

If there are error messages, please post them here.

Thanks.

---

### Post by beew on 2011-07-06
Well what is new, this is almost expected especially with the drastic change of UI. Instead of wasting your time trouble shooting a failed upgrade just back up your data and do a fresh install. Takes a lot less time and there is much less chance of screwing up. I really don't understand why so many people want to do thing the long and risky way with distro upgrade.

---

### Post by krbhnp on 2011-07-08
> **Rubi1200 said:**
> You can try the following commands in the terminal and see if it helps resolve the issue:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

If there are error messages, please post them here.

Thanks.

r@r-desktop:~$ sudo apt-get clean
[sudo] password for r: 
E: Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory
r@r-desktop:~$ sudo apt-get update
E: Archives directory /var/cache/apt/archives/partial is missing. - Acquire (2: No such file or directory)
r@r-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by krbhnp on 2011-07-08
> **seawolf167 said:**
> I'm not sure about the error - but regardless, I suggest doing a fresh install changing to Unity from Gnome.

Make a backup with [Clonezilla ]("http://www.clonezilla.org")just in case, then IMO the best thing to do would be to move /home to its own [separate partition ]("https://help.ubuntu.com/community/Partitioning/Home/Moving")then just reinstall / (root) with an install cd and all your settings, documents, files, etc. will still be there (on /home).

I am a newbie..I couldn't understand anything u said...could you tell that in a more easy way for me please? Thanks for the reply...

---

### Post by krbhnp on 2011-07-08
> **Rubi1200 said:**
> You can try the following commands in the terminal and see if it helps resolve the issue:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

If there are error messages, please post them here.

Thanks.

Thanks for the reply but I got the following error messages when I entered the commands:
(1)sudo apt-get clean    

Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory

(2)sudo apt-get update

Archives directory /var/cache/apt/archives/partial is missing. - Acquire (2: No such file or directory)

(3)sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pjd99 on 2011-07-08
Do you have another package manager (synaptic, software centre) running. If so, you need to close it before trying the apt-get commands.

Otherwise, an error may have occurred and the lock file is still present.

sudo rm /var/lib/dpkg/lock

---

### Post by pjd99 on 2011-07-08
> **beew said:**
> Well what is new, this is almost expected especially with the drastic change of UI. Instead of wasting your time trouble shooting a failed upgrade just back up your data and do a fresh install. Takes a lot less time and there is much less chance of screwing up. I really don't understand why so many people want to do thing the long and risky way with distro upgrade.

Well, why is the option available if it's so bad. I dist-upgraded (regretted ever since) because I had the system configured the way I wanted, and didn't want to do it all again from scratch. Figured that because I had installed 10.10 a month after release, that upgrading to 11.04 a month after release would be the smart thing to do. 

I was wrong. But that's not because dist-upgrade is inherently bad, it's because 11.04 is...

---

### Post by kanishkdudeja on 2011-07-08
> **pjd99 said:**
> Do you have another package manager (synaptic, software centre) running. If so, you need to close it before trying the apt-get commands.

Otherwise, an error may have occurred and the lock file is still present.

sudo rm /var/lib/dpkg/lock

If none of these are running, then try restarting your system.

And then run the commands and post the output if it works then.

---

### Post by krbhnp on 2011-07-08
> **kanishkdudeja said:**
> If none of these are running, then try restarting your system.

And then run the commands and post the output if it works then.

Well, I don't know anything about distros and blah blah...Please tell me in a layman's language from the beginning what I need to do...Thanks for the reply...

---

### Post by kanishkdudeja on 2011-07-08
Restart your system.

Then open up the terminal..

Run these commands one by one and post their output..

```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by krbhnp on 2011-07-08
> **kanishkdudeja said:**
> Restart your system.

Then open up the terminal..

Run these commands one by one and post their output..

```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

I got the following errors:
(1)sudo apt-get clean

Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory

(2)sudo apt-get update
Archives directory /var/cache/apt/archives/partial is missing. - Acquire (2: No such file or directory)
(3)sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by kanishkdudeja on 2011-07-08
Well, then im sorry, i dont know how to fix it.

Wait a little, somebody here on the forums should know the solution and will help you..:)

---

