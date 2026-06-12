---
title: "Ubuntu 10.10 doesnt exist?"
date: 2010-10-11
forum: General Help
---

### Post by Adrienk on 2010-10-11
```
adam@adam-laptop:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adam@adam-laptop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

```

Can some one explain?

---

### Post by MooPi on 2010-10-11
What are you currently using ?
try this in terminal ```
lsb_release -rd
```
Run this also less /etc/update-manager/release-upgrades
At the bottom of that output should read ```
prompt=normal
``` If it reads ```
prompt=lts
``` then your system will only look for lts upgrades

---

### Post by 3Miro on 2010-10-11
Have you done:
```
sudo apt-get update
```

Also, make sure you are running 10.04
```
uname -a
```
check for the kernel version. I believe 10.04 was using 2.6.33, on 10.10 it should be 2.6.35 (and I also know there is an easier way to check the version of your release, but I cannot remember it right now).

---

### Post by roggenschrotbrot on 2010-10-11
```
cat /etc/lsb-release
```?

to late. but mine is the easier way mentioned :P

---

### Post by Adrienk on 2010-10-11
This is what I get for almost failing operating systems class

A) 10.04 <- What I am currently running
B) how do I update that file to make it say: normal?
C) I only have 8.2 gigs of space between "/" and "/home" (so 16.4 in total) - is that enough space to run the upgrade?

---

### Post by fooman on 2010-10-11
why not use the update manager to upgrade?

go to > system > administration > update manager

near the top up the window that opens,  it will show that a new version is available (10.10)....click "upgrade"

it will start the procedure and load the new sources,  then before it performs the upgrade,  it will show you how much space will be needed.  this will depend on what you have already installed in the old version.  you will have the option of opting out before commiting to the upgrade.

hope that helps.

---

### Post by Adrienk on 2010-10-11
Do you really think I would be here asking these newb questions I should already know if I already didnt try that?

It states my system is up to date yet im running 10.4

---

### Post by ephmanjmm on 2010-10-11
System | Administration | Update Manager

Click the Settings button.
Select the Updates tab.
Change the drop down box to Normal Releases.

---

### Post by yetiman64 on 2010-10-11
To get the upgrade to 10.10 button in Update Manager in 10.04 (an LTS release), first go to System > Administration > Software Sources > Updates tab and set "Release Upgrade" to Normal releases. Close software sources, open Update Manager and the upgrade to 10.10 button is available.

> It states my system is up to date yet im running 10.4     Probably because an LTS release only looks to upgrade to another LTS by default. The above will change that and give you the update button.

---

### Post by MooPi on 2010-10-11
> **Adrienk said:**
> This is what I get for almost failing operating systems class

A) 10.04 <- What I am currently running
B) how do I update that file to make it say: normal?
C) I only have 8.2 gigs of space between "/" and "/home" (so 16.4 in total) - is that enough space to run the upgrade?
To change that file ```
gksu gedit /etc/update-manager/release-upgrades
```At the very bottom of the file it should list your , prompt=normal/lts .
Change to normal and you should be able to ubdate to 10.10
If you run the command ```
sudo do-release-upgrade
``` in terminal it will tell you how much space is required

---

