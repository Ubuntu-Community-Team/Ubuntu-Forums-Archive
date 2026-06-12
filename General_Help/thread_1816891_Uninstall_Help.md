---
title: "Uninstall Help"
date: 2011-08-02
forum: General Help
---

### Post by Hubunntu on 2011-08-02
I installed Kubuntu 11.4 (64 bit). But now I can't update it, all time it shows error :confused: Now I wanna uninstall Kubuntu and also wanna install Ubuntu :D Please tell me how to uninstall kubuntu without losing any data. 
**I'm also user of Windows 7. I installed kubuntu as duel boot. now need to uninstall kubuntu without making any change of my laptop and wanna intall Ubuntu as duel boot. expert bro pls help me :(

---

### Post by 3Miro on 2011-08-02
If you installed the system as Dual-Boot (as opposed to Wubi), then you should be able to just install Ubuntu over Kubuntu. Get an Ubuntu liveCD or USB and when you have to select the partitioning scheme, select "advanced" and tell it to install Ubuntu on top of Kubuntu (effectively erasing Kubuntu).

Also, have you tried fixing the package issue. If you fix that one, you will be able to run both Gnome and Unity (the Ubuntu environment) and KDE (the Kubuntu environment) on the same machine with just logout/login.

---

### Post by Hubunntu on 2011-08-02
If I follow your process ,is there any risk to lose widows 7, Cause I stored all data there. When I update Kubuntu , I face problem about fixing the package issue. Please tell me details about fixing the package issue. And tell me details about installing  Ubuntu on top of Kubuntu.

---

### Post by Mark Phelps on 2011-08-02
OK, first of all, it's by definition IMPOSSIBLE to uninstall any OS without losing data -- at the very least, you will lose the files installed with that OS!

So, if you want to retain files you presently have in Kubuntu, you will need to copy them off to an external drive before you remove Kubuntu and/or install Ubuntu.

If you installed Kubuntu to its own separate partition (NOT a Wubi install), BEFORE you attempt to install Ubuntu, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you need to repair the Win7 boot loader.

IF you're really nervous about losing stuff in Win7, then you need to back it off BEFORE you attempt to remove Kubuntu or install Ubuntu.  You should go to the Macrium Reflect website and download and install the FREE version.  After that, use the option to create and burn a Linux Restore CD.  Also, image off Win7 to an external drive.  NOW, you can fully restore Win7 should anything happen to it.

Sorry ... just got a call ... have to run.

---

### Post by Hubunntu on 2011-08-03
I installed Kubuntu to its own separate partition, So now if I format that partition (Kubuntu installed Partition) , is it possible to remove kubuntu?  :confused:   if possible , then I will remove kubuntu, then I´ll install ubuntu.   

Or if not possible to format the partition, So is it possible to install ubuntu along with Kubuntu and win7 ?a

---

### Post by 3Miro on 2011-08-03
When you format a partition you lose all data on that partition. To install an OS on a partition, you need to format that partition.

You can install Ubuntu on the partition of Kubuntu, which will delete Kubuntu and replace it with Ubuntu. If you don't touch the Windows 7 partition, Windows 7 should be fine.

If you want Ubuntu and Kubuntu both installed, you need to create a separate partition for Ubuntu. Then you will have partitions for Windows 7, Ubuntu and Kubuntu and all three can live side-by-side.

The main difference between Kubuntu and Ubuntu is the Desktop Environment, one uses KDE and the other one Gnome+Unity. You can have both KDE and Gnome+Unity installed on the same installation of Ubuntu or Kubuntu (just make sure you have enough HDD space). This is a good way to experience different DE before you can decide which one you like the most. To see how to run different DE check [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

A word of caution: Whenever you mess with partitions, it is always possible to click something wrong, resulting in loss of important data. You should always backup ALL important files before you try to install OS or reinstall OS or repartition HDD.

PS If you just format the Kubuntu partition, you will remove Kubutu, but you will also need to repair the Windows 7 bootloader (otherwise you cannot boot your machine). If you want to just remove Kubuntu, then boot into Windows, repair the bootloader and then format the Kubuntu partition. I think this is the right procedure for Windows, although I don't use Windows so I am not sure.

---

### Post by Hubunntu on 2011-08-03
Thanks a lot for your support. Now I'm gonna install Ubuntu on the partition of Kubuntu, according to your info , this process will only make  change Kubuntu partition, and can't make any harm on others partition . so win 7 will be ok?  
My all info and soft are installed on win 7. Thats why I need protection on win 7 :)
Anyways which Ubuntu version should I use. 11.4 Beta or 10.4 LTS ? when Ubuntu 11.4 LTS will be available  ? I'm looking for latest one :D

---

### Post by 3Miro on 2011-08-03
> **Hubunntu said:**
> 
Anyways which Ubuntu version should I use. 11.4 Beta or 10.4 LTS ? when Ubuntu 11.4 LTS will be available  ? I'm looking for latest one :D

You got the numbering wrong. 10.04 is an LTS release supported for another two years. 11.04 is not a beta, but it will never become an LTS either. Next LTS release would be 12.04 coming next April.

Ubuntu is numbered after month/year, 10.04 means April 2010. Every 6 months Ubuntu has a new release, 10.04, 10.10, 11.04 ... Releases are normally supported for 18 months and every release is considered "Stable", however, every 2 years there are the LTS releases which are supported for 32 months. LTS are intended to be more stable from the beginning (they contain fewer experimental features) and over time they become very stable.

11.04 is overall less table than what you may normally see and that is why many people would call it "beta". 11.04 introduces the new Unity interface which some people like and some people hate. 11.04 is something that you may or may not like.

10.04 is currently the most stable Ubuntu and it should give you the least amount of trouble. 10.04 uses the old Gnome 2 interface.

If you feel somewhat adventurous, try 11.04 and if you don't like Unity (or you find it unstable), you can either run "Classic (No Effects)" mode  or reinstall 10.04. If you don't want to take any chances, go for 10.04.

---

### Post by Hubunntu on 2011-08-03
You are great , Thanks. Sorry for my lack of knowledge. I'll go for 10.04 LTS. :popcorn:
Please help me to repair Kubuntu , it shows error about fixing package issue, whenever I update kubuntu. how to solve it ? if I can fix the problem, I don't need to remove kubuntu :D

---

### Post by 3Miro on 2011-08-03
If you open the Konsole (find it with the search option), then you can type:

```
sudo apt-get update && sudo apt-get upgrade
```

This will ask for a password and it will update your system (answer yes if it is asking for permission).

Hopefully this will fix the issue. If not, copy and paste the result of the command here.

---

### Post by Hubunntu on 2011-08-03
I followed your last instraction, but it updated almost 14 MB ,but then Konsol shows below error, what to do now?
******
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

******

---

### Post by Hubunntu on 2011-08-03
When I use "sudo apt-get update && sudo apt-get upgrade " code  it started update automatically , then after 14 MB done it shows following error. what to do now ? :confused:
---------------------------------------------------------------------------------------
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by 3Miro on 2011-08-03
When you get an error, it is best to Google it. Try the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1764380](http://ubuntuforums.org/showthread.php?t=1764380)

Basically try the following commands one at a time. This would clean the repository cache.

```
sudo rm /var/lib/apt/lists/* 
sudo apt-get clean 
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by Hubunntu on 2011-08-03
Yeaah  finall solved the problem ,  Thanks a lottttttttttttttt    :)

---

### Post by 3Miro on 2011-08-03
> **Hubunntu said:**
> Yeaah  finall solved the problem ,  Thanks a lottttttttttttttt    :)

Glad to help, if you don't have any more questions please mark the thread as "Solved".

---

### Post by Hubunntu on 2011-08-04
I'm facing problem installing VLC and google and skype , it shows following error :confused:

------------------------------
 p, li { white-space: pre-wrap; }  The following packages have unmet dependencies:
chromium-browser: Depends: libnss3-1d (>= 3.12.3) but it is not going to be installed
vlc: Depends: vlc-nox (= 1.1.11-2~ppa1) but it is not going to be installed
Recommends: vlc-plugin-notify (= 1.1.11-2~ppa1) but it is not going to be installed
Recommends: vlc-plugin-pulse (= 1.1.11-2~ppa1) but it is not going to be installed

-------------------------------

here is my  package list
----------------------------------
# deb cdrom:[Kubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty universe
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

