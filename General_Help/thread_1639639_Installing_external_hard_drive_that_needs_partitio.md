---
title: "Installing external hard drive that needs partitioning"
date: 2010-12-06
forum: General Help
---

### Post by rjmiller on 2010-12-06
OK guys and gals, I'm still a noob at Linux so bear with me. I'm running Ubuntu Lucid Lynx and want to use an external hard drive to back up my system. I bought a 500 GB Western Digital My Book Essential (the same size as my hard drive). The problem is it's only formatted for Windows or Mac. I've read that the drive can be partitioned with GParted and have printed out the instructions to do so. My question is: will the WD SmartWare software work with Linux or do I need to download something else to actually run the drive. I figured I'd better ask some questions before doing anything permanent to the external drive.

---

### Post by oldfred on 2010-12-07
Welcome to the forums.

I think you will be starting another reoccurring discussion as just about everyone has a different idea. Some recommend tar as that is good at compressing and has a lot of parameters to allow compressing and saving data.

Some recommend full images.
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)

aptoncd for installed applications:
Location of downloaded debs
/var/cache/apt/archives/

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

I backup my personal files to DVD periodically and have a rsync script to copy data over to a backup directory since I usually want to recovery one file not the entire folder or system.
I have multiple working installs, old, current, beta versions of Ubuntu on my 3 hard drives, a bootable USB with a full install, a bootable USB with multiple Ubuntu & other repair ISOs. I also periodically copy data to my portable using NFS.

But I just save my data with rsync and if a drive fails plan on a full install adn restore of /home & my data. My rsync also includes a dpkg list of all installed apps and a copy of bootinfo script to know how my system was partitioned and what was installed where.

---

### Post by rjmiller on 2010-12-07
I want to create a backup of my system so, if it crashes, I can use the backup to either fix the system or replace it then reload all my files and settings. It seems like I'm going to have to partition the external drive and install a program to create and manage the backup. If I'm reading the article about backing up your system correctly, it sounds like drive imaging might be the way to go. Is this the simplest and easiest way to create the type of backup I want or did I miss something?

---

### Post by oldfred on 2010-12-08
I think so, that would be clonezilla or remastersys.

I still think it is just easier to reinstall and reload data. Backup of system is not really all that different from an install CD. It probably depends on how much you customize your system. Most of my customization I have done from command line, listed in history and copied to a bash script so all I have to do is rerun it.

---

