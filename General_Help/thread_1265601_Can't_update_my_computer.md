---
title: "Can't update my computer"
date: 2009-09-13
forum: General Help
---

### Post by rannuG on 2009-09-13
Got it! I found an older thread where someone had a similar problem: [http://ubuntuforums.org/showthread.php?t=1248969](http://ubuntuforums.org/showthread.php?t=1248969)

> This was the answer
type this - sudo rm /var/lib/apt/lists/* -vf

then type this - sudo apt-get update

thanks for your help on the wayAll seems to be working fine now.
Thanks all for your help!


-



Hello, I got a problem with my Ubuntu 9.04.
Whenever I go to the Update Manager, Synaptic and Add/Remove, I get messages saying something's wrong:

Update Manager:
> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'Add/Remove:
> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'. I did try 'sudo apt-get update' and 'sudo apt-get install -f' but it didn't work at all. When doing so, this came up: > E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.Synaptic:
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages
E: Package list or condition list couldn't be parsed or opened.
E: _cache->open() failed, please report.I guess it might be my source list. Maybe there's something wrong with it?
> # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"Any help would be really apprecited.

---

### Post by NoaHall on 2009-09-13
Well, to solve it , put a "#" before the last line. However, you won't get any more direct updates from Wine. So it's only a temporary fix.

---

### Post by codemyster on 2009-09-13
Try removing the last line in your sources.list file, save it, and then try to apt-get update.

---

### Post by rannuG on 2009-09-13
When putting # before the last line, I get this:
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.when removing the last line, I get this:
> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
Hmm...

---

### Post by NoaHall on 2009-09-13
You have jaunty or interpid?

---

### Post by rannuG on 2009-09-13
Jaunty.

---

### Post by NoaHall on 2009-09-13
Can you run 

cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages

---

### Post by rannuG on 2009-09-13
Nope.
> $ cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages
cat: /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_: No such file or directory
cat: binary-i386_Packages: No such file or directory


---

### Post by NoaHall on 2009-09-13
Hm. I have no idea what the code for iceland is.

Run

```


ls /var/lib/apt/lists/ | grep ubuntu_dists_jaunty_partner
```

---

### Post by rannuG on 2009-09-13
> $ ls /var/lib/apt/lists/ | grep ubuntu_dists_jaunty_partner
archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages


It might be IS.

---

### Post by NoaHall on 2009-09-13
Hm, perhaps. Well, this should see.
now do 
```
 cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages | grep fail 
```

and 
```
 cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages | grep Error 
```

---

### Post by rannuG on 2009-09-13
> $  cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages | grep fail
cat: /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_: No such file or directory
cat: binary-i386_Packages: No such file or directory
> $  cat /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_ binary-i386_Packages | grep Error
cat: /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_: No such file or directory
cat: binary-i386_Packages: No such file or directory
No such files or directories.

---

### Post by NoaHall on 2009-09-13
Hm. ls said there was.. Anyway, maybe you should try putting a "#" before a line one at a time.

---

### Post by rannuG on 2009-09-13
> **NoaHall said:**
> Anyway, maybe you should try putting a "#" before a line one at a time.

I tried that, but it always ended up the same:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```Can't uninstall Wine either, same thing happens there, except the Problem with MergeList is /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages

---

### Post by NoaHall on 2009-09-13
The problem, as far as I can tell, is that the mergeList file doesn't exist. I guess it will be fixed by getting the file, but as I have 64 bit not 32 bit, I can't help you.

---

### Post by rannuG on 2009-09-13
Got it! I found an older thread where someone had a similar problem: [http://ubuntuforums.org/showthread.php?t=1248969](http://ubuntuforums.org/showthread.php?t=1248969)

> This was the answer
type this - sudo rm /var/lib/apt/lists/* -vf

then type this - sudo apt-get update

thanks for your help on the way

All seems to be working fine now.
Thanks all for your help!

---

