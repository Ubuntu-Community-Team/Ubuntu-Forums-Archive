---
title: "how to backup entire system? [HELP]"
date: 2011-04-19
forum: General Help
---

### Post by D0nJ0seph on 2011-04-19
[U][I][B]EDITED. THIS ARE THE PROPOSALS TO BACKUP YOUR SYSTEM
[/B][/I][/U]
The first one was proposed by [ashickur.noor]("http://ubuntuforums.org/member.php?u=1133893") this is the post:
> **ashickur.noor said:**
> Use remastersys. By using then you can  make customdistro and also custombackup. Custdistro means it will backup  your all / thing without /home and customback means it will backup all  thing in /. It can create an ISO if your backup is less then 4  GB.
To achieve this, [mike555]("http://ubuntuforums.org/member.php?u=107656") said to install some programs, then [ashickur.noor]("http://ubuntuforums.org/member.php?u=1133893") corrected him. this is the post:
> **ashickur.noor said:**
> [QUOTE=mike555;10697113]If your going to use Remastersys ,install Unity  and Unity-frontend-gtk first ,that way your .iso will be installable  after burning it ...I think it should be ubiquity not Unity.[/QUOTE]
I used remastersys to create a "Custom Live CD" of ubuntu. In that way, i can install Ubuntu anywere with the programs i allready have, and not sharing any of my files, only programs. This worked great because a friend asked me if i could install ubuntu in her computer but with all the programs i have.

But, what i used to backup my system was [lmarmisa]("http://ubuntuforums.org/member.php?u=955260")'s proposal. This is the post:
> **lmarmisa said:**
> I recommend to use Clonezilla Live:

[http://www.clonezilla.org/clonezilla-live.php](http://www.clonezilla.org/clonezilla-live.php)
When i readed the official web page of this project, i thought it was useless because it says that the limitation is that the target disk must be equal or bigger in size than the total amount of data you want to back up. My entire system weighs 37GiB. So i asked if there was a way to change this. This is what [Imarmisa]("http://ubuntuforums.org/member.php?u=955260") respond
> **lmarmisa said:**
> Clonezilla supports two modes:

1) Cloning mode: an exact replica of a disk (or partition) is made into a  target disk (or partition). The target disk (or partition) must be  equal or bigger than the source disk.

2) Backup. A complete backup of a disk (or partition) is made. There is  no limitation about the size of the disk (or partition) where the backup  files are stored. Limitation applies to the size of disk (or partition)  where the backup is restored. After a restoration, the content of the  destination disk (or partition) is an exact replica of the source disk  or partition.
Now i have my backup in several disk. THANKS A LOT!

So, because i allready achieve what i was looking for, i didn't test the rest of the proposals, but i'll add them also so you can know them. 

We have [nmaster]("http://ubuntuforums.org/member.php?u=851166")'s solution:
> **nmaster said:**
> i really like fsarchiver: [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

just take a look at the quickstart guide.  its easy to use and has been effective for me in the past.

Then we have something more complicated but might work aswell. This is [Oldfred]("http://ubuntuforums.org/member.php?u=852711")'s post:
> **oldfred said:**
> I figure why backup Ubuntu system, I am just  going to reinstall. But you need to backup /home, list of installed  apps, custom system wide configurations in /etc and perhaps a few more  things.

Someone suggested this:
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

sudo cp /etc/apt/sources.list ~/sources.list.backup

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files

I also run a copy of boot info script to have booting configuration and hardware info:
HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
 udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table  contents in a friendly format. This DMI or SMBIOS contains a description  of the system's hardware components and other useful information such  as serial numbers and BIOS revision. This is a really powerful command.

It may seem like a lot of work, but it is part of normal backup. I also  use it for each new install every 6 months. The full image gets dated  and is worth having as a starting point, but regular backups are  important also.
And he's right! seems like a lot of work! But i think is one of the best if you know what you're doing and choose manually what you want to backup. THANKS!

Then we have [Smithark]("http://ubuntuforums.org/member.php?u=1204949")'s post.
> **smithark said:**
> or you could use "Back in Time" or "Dejavu".  they are quite simple and user friendly. choose the one that suits you  the most.


And basically that's all. I also recieved an intersting and very usefull tip from [Josephmills]("http://ubuntuforums.org/member.php?u=1238005"). This is the post:
> **josephmills said:**
> You know when you get Ubuntu you also git **sorry get** 2 gb of free online of storage through UbuntuOne thought that I would friendly put that in the mix.:smile:
**EDIT:**

_**[COLOR=Red]THANKS TO ALL FOR THE QUICK RESPONSES AND USEFULL TIPS![/COLOR]**_



_***ORIGINAL POST***_

Hello people.
Well, i've made a lot of changes to ubuntu 10.04 and now i love it! It does everything i'll want from any computer. This took me a lot of time, follow several tutorials and destroy the entire system a couple of times. The last one is a BIG problem because restoring my system to the state before i ****** all up takes some time again :/

Do any of you guys know how to backup all my system settings, programs and files? So that if i corrupt my system again i can restore it to be exactly as my current state?

THANKS IN ADVANCE!

---

### Post by ashickur.noor on 2011-04-19
> **D0nJ0seph said:**
> Hello people.
Well, i've made a lot of changes to ubuntu 10.04 and now i love it! It does everything i'll want from any computer. This took me a lot of time, follow several tutorials and destroy the entire system a couple of times. The last one is a BIG problem because restoring my system to the state before i ****** all up takes some time again :/

Do any of you guys know how to backup all my system settings, programs and files? So that if i corrupt my system again i can restore it to be exactly as my current state?

THANKS IN ADVANCE!
Use remastersys. By using then you can make customdistro and also custombackup. Custdistro means it will backup your all / thing without /home and customback means it will backup all thing in /. It can create an ISO if your backup is less then 4 GB.

---

### Post by lmarmisa on 2011-04-19
I recommend to use Clonezilla Live:

[http://www.clonezilla.org/clonezilla-live.php](http://www.clonezilla.org/clonezilla-live.php)

---

### Post by mike555 on 2011-04-19
If your going to use Remastersys ,install Unity and Unity-frontend-gtk first ,that way your .iso will be installable after burning it ...

---

### Post by smithark on 2011-04-19
or you could use "Back in Time" or "Dejavu". they are quite simple and user friendly. choose the one that suits you the most.

---

### Post by ashickur.noor on 2011-04-20
> **mike555 said:**
> If your going to use Remastersys ,install Unity and Unity-frontend-gtk first ,that way your .iso will be installable after burning it ...
I think it should be ubiquity not Unity.

---

### Post by oldfred on 2011-04-20
I figure why backup Ubuntu system, I am just going to reinstall. But you need to backup /home, list of installed apps, custom system wide configurations in /etc and perhaps a few more things.

Someone suggested this:
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

sudo cp /etc/apt/sources.list ~/sources.list.backup

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files

I also run a copy of boot info script to have booting configuration and hardware info:
HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
 udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

It may seem like a lot of work, but it is part of normal backup. I also use it for each new install every 6 months. The full image gets dated and is worth having as a starting point, but regular backups are important also.

---

### Post by D0nJ0seph on 2011-04-20
WOW
thanks to all for the quick responses. I'll try remastersys. THANKS AGAIN!. I'll post my results later

---

### Post by josephmills on 2011-04-20
> **oldfred said:**
> I figure why backup Ubuntu system, I am just going to reinstall. But you need to backup /home, list of installed apps, custom system wide configurations in /etc and perhaps a few more things.

Someone suggested this:
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

sudo cp /etc/apt/sources.list ~/sources.list.backup

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files

I also run a copy of boot info script to have booting configuration and hardware info:
HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
 udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

It may seem like a lot of work, but it is part of normal backup. I also use it for each new install every 6 months. The full image gets dated and is worth having as a starting point, but regular backups are important also.
+1 thanks):P

---

### Post by D0nJ0seph on 2011-04-20
^^^
This sounds complicated but might work. I'm not that "pro" in ubuntu so i'll try this when i learn more about the programming language.

> **smithark said:**
> or you could use "Back in Time" or "Dejavu". they are quite simple and user friendly. choose the one that suits you the most.
This is a good option, but i'll prefer to complete backup so, if i buy a new computer, i can copy my entire system easily

> **lmarmisa said:**
> I recommend to use Clonezilla Live:

[http://www.clonezilla.org/clonezilla-live.php](http://www.clonezilla.org/clonezilla-live.php)

mmm, this look great. But i can only backup into something that can hold the same size or bigger of my hard disk :/

> **ashickur.noor said:**
> Use remastersys. By using then you can make customdistro and also custombackup. Custdistro means it will backup your all / thing without /home and customback means it will backup all thing in /. It can create an ISO if your backup is less then 4 GB.

This by now sounds like the best option, i'll just check if i can backup in several disks and not only 1.

> **ashickur.noor said:**
> I think it should be ubiquity not Unity.

THANKS!

---

### Post by lmarmisa on 2011-04-20
> **D0nJ0seph said:**
> ^^^

mmm, this look great. But i can only backup into something that can hold the same size or bigger of my hard disk :/



That limitation of Clonezilla applies only to the cloning feature. The limitation has no effect in case of a complete backup.

---

### Post by D0nJ0seph on 2011-04-20
> **lmarmisa said:**
> That limitation of Clonezilla applies only to the cloning feature. The limitation has no effect in case of a complete backup.

So i can backup all my settings, programs and files in several disks? what's the difference between clonning and backup?

What i understand by backup is just to copy files, and of clone is to copy all, settings, programs and, well, ALL!

---

### Post by nmaster on 2011-04-20
i really like fsarchiver: [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

just take a look at the quickstart guide.  its easy to use and has been effective for me in the past.

---

### Post by ashickur.noor on 2011-04-20
> **D0nJ0seph said:**
> So i can backup all my settings, programs and files in several disks? what's the difference between clonning and backup?

What i understand by backup is just to copy files, and of clone is to copy all, settings, programs and, well, ALL!
By using remastersys you can share your iso with other, which they can install as modify Ubuntu. I don't know about clonezilla, I think It may be work for same PC only. But for remastersys I am sure that It will work for all PC.

---

### Post by lmarmisa on 2011-04-20
> **D0nJ0seph said:**
> So i can backup all my settings, programs and files in several disks? what's the difference between clonning and backup?

What i understand by backup is just to copy files, and of clone is to copy all, settings, programs and, well, ALL!

Clonezilla supports two modes:

1) Cloning mode: an exact replica of a disk (or partition) is made into a target disk (or partition). The target disk (or partition) must be equal or bigger than the source disk.

2) Backup. A complete backup of a disk (or partition) is made. There is no limitation about the size of the disk (or partition) where the backup files are stored. Limitation applies to the size of disk (or partition) where the backup is restored. After a restoration, the content of the destination disk (or partition) is an exact replica of the source disk or partition.

---

### Post by josephmills on 2011-04-20
You know when you get Ubuntu you also git **sorry get** 2 gb of free online of storage through UbuntuOne thought that I would friendly put that in the mix.:)
**EDIT:**

---

### Post by D0nJ0seph on 2011-04-21
> **josephmills said:**
> You know when you get Ubuntu you also git **sorry get** 2 gb of free online of storage through UbuntuOne thought that I would friendly put that in the mix.:)
**EDIT:**

thanks! i didn't knew that.

---

