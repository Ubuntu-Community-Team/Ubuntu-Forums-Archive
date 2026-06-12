---
title: "backup strategy."
date: 2011-07-17
forum: General Help
---

### Post by pjmlmas on 2011-07-17
Protocol
I would like to have weekly(occasionally daily) and monthly backups. I believe my monthly backup s/b full, and weekly s/b incremental/diff. I have external USB hard drive. Currently I have multiple partitions but would only need two to be backed-up.

1st: Cmd line should be able to do this, or should I use script/program that is more robust? I have seen some shell scripts that simply copy root leaving out some mounts.
2nd: How will the diff work if shell script? Have not seen much of this.
3rd: Say partition sda7  is "lost" for some reason. If I were to have copied root in Jul, and had weekly diff, I could simply repartition sda7, copy back full bu, copy diff bu? re-run grub2 and everything would 'work'?
If not, what steps should I have taken, AND what steps would be needed to rebuild sda7?
4th: How have you handled backups of audio/video (my working partitions are 4-6 gigs which I plan to backup, but data partitions  are 40,80,100 gigs...which I have no idea what strategy to use)
-Thanks!

---

### Post by oldfred on 2011-07-17
I do not have as much data as you do to backup. I periodically backup my data to DVDs so I have a copy that will not get overwritten with bad data. Then I use rsync to copy data more ofter to another drive.

I do not do full image backups. I assume I will just reinstall, since I can do that and reconfigure in about an hour.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

I have used this script and modified it for my use:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

This is what I do backup:
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

### Post by Feenix217 on 2011-07-17
I like using Ubuntu One. I have 10.10 on 5 PCs and run at least 2 at the same time. And when I fire up another one, I will log into Ubuntu One and then let the system do the backups for me.

Dave

---

### Post by pjmlmas on 2011-07-18
rsnapshot - this seems very promising as backup strategy. To anyone who has used this...so it will create full and incremental, keep n number of "snapshots". 
Is one able to define when a true full backup runs?
Since it is basically rsync, so what files would  I include from partition (say sda7). From what I have read so far, /mount s/b ignored.

---

