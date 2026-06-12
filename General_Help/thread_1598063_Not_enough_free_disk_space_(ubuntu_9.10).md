---
title: "Not enough free disk space (ubuntu 9.10)"
date: 2010-10-16
forum: General Help
---

### Post by agentfortyseven on 2010-10-16
hello everyone,
I am a complete noob using Ubuntu 9.10 for the past 6 months. I have a dual boot system i.e windows XP and Ubuntu 9.10. I never had any issue until I started getting the following warning message whenever I try to install updates from update manager. I can't even download other stuff from internet. Please help.

[B]Not enough free disk space

The upgrade needs a total of 173M free space on disk '/'. Please free at least an additional 63.1M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/B]

Emptying trash and using sudo apt-get clean did not help :(

---

### Post by zaphod777 on 2010-10-16
You are out of disk space go to "Applications -> Accessories -> Disk Usage Analyzer" 

Probably the easiest thing to do would be to backup and remove some of your large videos and music or any other large files.

---

### Post by agentfortyseven on 2010-10-16
I have installed Ubuntu on a 25 GB partition

---

### Post by agentfortyseven on 2010-10-16
I tried using Disk Usage Analyzer many times but couldn't figure out much in there. (like I said I'm a complete noob)

---

### Post by zaphod777 on 2010-10-16
Click scan filesystem and then the graph on the right side shows where your biggest files are. 

[http://www.thevarguy.com/2010/01/14/ubuntus-disk-usage-analyzer/](http://www.thevarguy.com/2010/01/14/ubuntus-disk-usage-analyzer/)

---

### Post by agentfortyseven on 2010-10-16
> **zaphod777 said:**
> You are out of disk space go to "Applications -> Accessories -> Disk Usage Analyzer" 

Probably the easiest thing to do would be to backup and remove some of your large videos and music or any other large files.

Thank you zaphod777 for your advice, moving my music and videos to other partitions would free upto 2 GB. But my real issue is "How can I run out of disk space when I'd installed Ubuntu on a 25 GB partion?"

---

### Post by cocokessler on 2010-10-16
25Gb is pretty small for most users.  You might consider upgrading your hard drive at some point in the near future. 500Gb drives are cheap these days.

---

### Post by zaphod777 on 2010-10-16
You will need to look through the app and see what folders are taking up your space. 25GB isn't that much these days I am using 103GB out of 140GB on my laptop.

I would check your "Downloads" directory or any of the folders you use for torrent files. You may have a whole folder full of incomplete torrent downloads.

---

### Post by agentfortyseven on 2010-10-16
[QUOTE=zaphod777;9980696]Click scan filesystem and then the graph on the right side shows where your biggest files are. 


scanning filesystem gave me the following result.

[B]/   100%   13.4GB   21 items
 > host    56.1%   7.5GB    4 items
 > home   19.2%   2.6GB    1 items 
 > usr   18.5%   2.5GB   10 items
[/B]
other folders are in MBs.

---

### Post by agentfortyseven on 2010-10-16
> **zaphod777 said:**
> You will need to look through the app and see what folders are taking up your space. 25GB isn't that much these days I am using 103GB out of 140GB on my laptop.

I would check your "Downloads" directory or any of the folders you use for torrent files. You may have a whole folder full of incomplete torrent downloads.

My download folder is empty and I don't use torrent at all :). Yeah you are right about 25GB not much, I'll try to make up for it someday.

---

### Post by alexan on 2010-10-16
Empty your trashbin
also

Terminal:
**sudo su**
then:

[b]rm /var/cache/apt/archives/*
rm /var/cache/apt/archives/partial/*
apt-get autoclean
apt-get install deborphan -y
aptitude purge `deborphan --guess-all`[/B]

---

### Post by agentfortyseven on 2010-10-16
> **cocokessler said:**
> 25Gb is pretty small for most users.  You might consider upgrading your hard drive at some point in the near future. 500Gb drives are cheap these days.

25GB isn't my hard disk space, its a partition of my HDD. I have a 250 GB disk n I used its 25GB partition for installing my Ubuntu 9.10 (dual boot alongside win XP)

---

### Post by cocokessler on 2010-10-16
> **agentfortyseven said:**
> 25GB isn't my hard disk space, its a partition of my HDD. I have a 250 GB disk n I used its 25GB partition for installing my Ubuntu 9.10 (dual boot alongside win XP)
You might consider using Gparted on the Ubuntu Live CD to reallocate your partitions.

Instructions can be found [HERE.]("https://help.ubuntu.com/community/HowtoPartition?highlight=((GParted))")

---

### Post by agentfortyseven on 2010-10-16
> **alexan said:**
> Empty your trashbin
also

Terminal:
**sudo su**
then:

[B]rm /var/cache/apt/archives/*
rm /var/cache/apt/archives/partial/*
apt-get autoclean
apt-get install deborphan -y
aptitude purge `deborphan --guess-all`[/B]

I get the following output when I run the above commands in the terminal.[B]

rm /var/cache/apt/archives/*
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

[/B][B]rm /var/cache/apt/archives/partial/*
rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory

root@ubuntu:/home/hitman# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@ubuntu:/home/hitman# apt-get install deborphan -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
deborphan is already the newest version.
deborphan set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
root@ubuntu:/home/hitman# aptitude purge `deborphan --guess-all`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  firefox-3.5{p} firefox-3.5-branding{p} firefox-3.5-gnome-support{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 35 not upgraded.
Need to get 0B of archives. After unpacking 397kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 206877 files and directories currently installed.)
Removing firefox-3.5 ...
Purging configuration files for firefox-3.5 ...
Removing firefox-3.5-branding ...
Removing firefox-3.5-gnome-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

[/B]Thanks for your help, but I guess this didn't helped either.

---

### Post by agentfortyseven on 2010-10-16
> **cocokessler said:**
> You might consider using Gparted on the Ubuntu Live CD to reallocate your partitions.

Is that gonna help? Will it screw-up my installed applications? Can you please elaborate on how to use it(safely:))?

---

### Post by cocokessler on 2010-10-16
> **agentfortyseven said:**
> Is that gonna help? Will it screw-up my installed applications? Can you please elaborate on how to use it(safely:))?
Gparted is pretty safe.  That being said, you should most certainly **back up** your stuff before using it.  I modified my other post to include a link to instructions that will help you to use it safely.  I have used it several times without screwing up anything.  :)

---

### Post by agentfortyseven on 2010-10-16
> **cocokessler said:**
> You might consider using Gparted on the Ubuntu Live CD to reallocate your partitions.

Instructions can be found [HERE.]("https://help.ubuntu.com/community/HowtoPartition?highlight=%28%28GParted%29%29")

sorry... forgot to see the link u gave, my bad.

---

### Post by agentfortyseven on 2010-10-16
> **cocokessler said:**
> Gparted is pretty safe.  That being said, you should most certainly **back up** your stuff before using it.  I modified my other post to include a link to instructions that will help you to use it safely.  I have used it several times without screwing up anything.  :)

Thanks, I will try it out hope it would help.

---

### Post by agentfortyseven on 2010-10-16
Any other suggestions other than G parted?

---

