---
title: "Convert 32-bit to 64-bit."
date: 2011-05-05
forum: General Help
---

### Post by satyanash on 2011-05-05
Hi,
I know this may sound stupid or too far-fetched but i need to get this done. My home box is a Ubuntu Lucid 32-bit(i686) which was a clone from my office computer. I dint know that it was a 32-bit one, just assumed it to be 64-bit. Now after 6 months i realized that the system is in fact 32-bit.
I have set it up as I wanted for the past 6 months with all the extra software,tweaks etc. I require. Now I need to convert it to 64-bit. Is there any way to do that without reinstalling the system.

I don't have a separate home partition.

Can I just copy over all files from my home folder to a new 64-bit EXT4 partition using the live CD and then mount it as the Home partition in a fresh 64-bit installation and reinstall all the software, thus bringing back all of my configurations? Does this partition need to be primary one?

I was planning on upgrading to Natty, but I think it'll be better to convert to 64-bit before upgrading.

Satyajeet:popcorn:

---

### Post by Sef on 2011-05-05
> Now I need to convert it to 64-bit. Is there any way to do that without reinstalling the system.

No. You must reinstall the system. No way exists to convert a 32-bit system to a 64-bit system.

---

### Post by satyanash on 2011-05-05
Okay, how do i maintain the configuration? Will any of the ways i mentioned work?

---

### Post by satyanash on 2011-05-05
> **Sef said:**
> No. You must reinstall the system. No way exists to convert a 32-bit system to a 64-bit system.

Also [http://www.linux.com/archive/feature/123800](http://www.linux.com/archive/feature/123800)
Just something I found out while searching.

---

### Post by satyanash on 2011-05-06
bump?

---

### Post by HereInOz on 2011-05-06
Regarding the upgrading of Fedora which you found, you are welcome to try it with Ubuntu.  Just remember, if it breaks, you get to keep all the pieces.

I would go through the process of creating a separate /home folder, in a separate partition, 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
then re-install Ubuntu 64 in the system partition, being very careful that you do NOT format the partition containing the /home folder.  That gives you the best chance of keeping your settings and data.

---

### Post by satyanash on 2011-05-06
OKay, but the fresh 64-bit system that I'll be installing should be 11.04 directly? or install 10.04 64-bit and then upgrade to 11.04, because the home folder config. will be for 10.04 right? And as of the home folder, can it exist on a logical partition instead of a primary one?

---

### Post by oldfred on 2011-05-06
Linux does not care if primary or logical. Usually best to reserve one or two primary partitioins in case you want windows or some system that needs primary in the future. But do not make all partitions logical either.

I keep my old 32bit install when I converted to 64bit. Since I  just have a home system, I do not do full image backups but do backup everything I may need to reinstall quickly. And I have learned as I always do clean installs but keep old partition and find occasionally I need to reboot back in old install to find something.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

---

### Post by TerminX on 2011-05-11
I successfully upgraded an 11.10 Oneiric devel install from 32-bit to 64-bit last night.  It's not impossible, but it would have been a rather spectacular failure if I didn't have busybox-static, regex knowledge and about 10 years of experience with dpkg beforehand.

I wouldn't recommend the faint of heart even attempt to wrap their heads around the kind of hackery required here.

---

### Post by freedomAboveAll on 2012-10-20
> **HereInOz said:**
> 
I would go through the process of creating a separate /home folder, in a separate partition, 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
then re-install Ubuntu 64 in the system partition, being very careful that you do NOT format the partition containing the /home folder.  That gives you the best chance of keeping your settings and data.

Thank you for suggesting this.

I successfully went from 12.0.4.1 32-bit to 64-bit using this idea.

Two possible gotchas I encountered were:

[LIST]
[*]my new home folder did not keep my modified dates (fixed by copying the files of concern from the backup home folder )  and 
[*]after the 64-bit install I had go to into recovery as root , mount the /home partition, do "mount -rw -o remount /" to make writeable, and "chown -R" my home folder to my new user.
[/LIST]

hth someone.

---

### Post by overdrank on 2012-10-20
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

