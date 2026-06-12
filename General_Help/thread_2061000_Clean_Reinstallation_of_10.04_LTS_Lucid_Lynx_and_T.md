---
title: "Clean Reinstallation of 10.04 LTS Lucid Lynx and Then Customize."
date: 2012-09-21
forum: General Help
---

### Post by histamineblkr on 2012-09-21
Ubuntu community I need your help. 

I searched awhile back and tried to find what I was looking for but didn't find it. I searched tonight and couldn't find what I was looking for. It may be I'm not sure "what" exactly I need to search for on these threads so if after reading this you can just point me at thread that's already covered this, thank you.

Here is what I would like to do. I would like to do a clean new reinstallation of 10.04LTS Lucid Lynx BUT I would like to retain all the things I have customized, installed, tweaked, scripted, etc, etc. Then after the new clean install I would like to go through all my things I have done and decide what I want to put back into the new installation. For example, I have many packages installed but I do not want all of them. I'm guessing there is some "apt-cache list" or similar command that gives you a list of every package installed. Also I have customized my GRUB so there is a nice pic in the background and customized the font color and so on. Some things needed to be customized or tweaked as root. A simple copy of the /home drive isn't going to be enough. I have virtualbox, netbeans, caffeine, docky, and many things that probably have some config file ".netbeans" or ".docky" that may or may not be in the /home directory. 

I am hoping someone can give me a guide line or step by step of how to get everything into a manageable location and be able to work with it. 

I am also thinking about separately partitioning directories when I freshly install, I would follow this: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
would this help for future reinstalls of having things separated and easier to work with?

---

### Post by ranger1021994 on 2012-09-21
1: )
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

2: )
[http://cpuug.org/index.php?topic=219.0](http://cpuug.org/index.php?topic=219.0)


This should take care of all installed packages.
If u do not wish to redownload all packages again then go to
> /var/cache/apt/packages and copy all your .debs
and then after installing "Lucid" again then reinstall them :)

Hope this helps :) :)

---

### Post by oldfred on 2012-09-21
+1 on ranger1021994 links. I use the dpkg command to export list and reinstall.

But I found after several upgrades to new versions I was installing a lot of old applications. Like python2.5. With 12.04 now it is LibreOffice not OpenOffice and you do not need both. 

The dpkg list is just a text file that you can edit, but it is long as it includes every dependency also. I have installed and use aptitude to get a list of top level apps only but do not know how to use just that list to reinstall. Some sort of awk command would work but I do not know details.

Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

All your settings should be in /home. Only if you made some system wide hardware settings to network configuration or video and those type would be in /etc.

Servers may have other folders off root for database, web or other applications.

---

### Post by histamineblkr on 2012-09-22
> **ranger1021994 said:**
> 1: )
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

2: )
[http://cpuug.org/index.php?topic=219.0](http://cpuug.org/index.php?topic=219.0)


This should take care of all installed packages.
If u do not wish to redownload all packages again then go to
 and copy all your .debs
and then after installing "Lucid" again then reinstall them :)

Hope this helps :) :)

Ah this should work perfectly for the packages. How do I tar a directory and include all of my hidden files? I'll try to google again when I get a chance but if you know of the top of your head that would be great. 

> **oldfred said:**
> +1 on ranger1021994 links. I use the dpkg command to export list and reinstall.

But I found after several upgrades to new versions I was installing a lot of old applications. Like python2.5. With 12.04 now it is LibreOffice not OpenOffice and you do not need both. 

The dpkg list is just a text file that you can edit, but it is long as it includes every dependency also. I have installed and use aptitude to get a list of top level apps only but do not know how to use just that list to reinstall. Some sort of awk command would work but I do not know details.

Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

All your settings should be in /home. Only if you made some system wide hardware settings to network configuration or video and those type would be in /etc.

Servers may have other folders off root for database, web or other applications.

I'm thinking about just copying the directories I know I have changed like /boot, grub, /home, and I think there is a couple others. If I tar them all to an external, I can pick out all the config files and things I have changed and just drop them in or edit the new ones to match. Can you export your cron jobs?

---

### Post by ranger1021994 on 2012-09-22
To create a tar click on folder containing all your files and right click and select compress,select your favourable format

---

### Post by histamineblkr on 2012-09-22
> **ranger1021994 said:**
> To create a tar click on folder containing all your files and right click and select compress,select your favourable format

Oh thank you. Do you know the command line tar command to include all your hidden folders?

---

### Post by oldfred on 2012-09-22
I have never used tar for backup.
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I prefer rsync. And the few files not in /home that I manually edit, I try to remember to copy to a folder in /home. Then my regular backup of /home includes those files without having to include a lot of other top level folders.

The files you may want to include should be the same regardless of how you do it.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

#I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
#Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by histamineblkr on 2012-09-23
> **oldfred said:**
> I have never used tar for backup.
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I prefer rsync. And the few files not in /home that I manually edit, I try to remember to copy to a folder in /home. Then my regular backup of /home includes those files without having to include a lot of other top level folders.

The files you may want to include should be the same regardless of how you do it.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

#I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
#Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Thank you very much. This is what I was looking for =)

---

### Post by histamineblkr on 2012-09-24
[QUOTE=oldfred;12254141]
I prefer rsync. And the few files not in /home that I manually edit, I try to remember to copy to a folder in /home. Then my regular backup of /home includes those files without having to include a lot of other top level folders.
[QUOTE]

I am familiar with the tar command but not with the rsync. I have seen it and kind of glanced over it, would you mind telling me why you use it and what advantages it has? I can go ahead and read the man page for it but would you mind showing me the command you use and why? 

Thank you.

---

### Post by oldfred on 2012-09-24
I have used compressed formats and had issues, so I now avoid them. But that only works now that hard drives are very large and for me the amount of data is smaller.

With rsync you can have one backup and have rsync only update the changed files. Makes it very quick, but if you damage a file and then back it up, you do not have any way to get it back. At work we used daily, weekly, monthly, annual tape backups and rotated the tapes. I do not remember exact schedule but dailies were not saved for a long time. I will backup to DVD periodically so I do have a copy that is saved. 

I have also seen users use date in rsync script save location to make multiple copies like the older grandfather, father, son backup rotation. Or have 3 copies (or more depending on space) backed up. But if backing up to one drive, a drive failure can cause loss of all backups.

I used this simple script, but of course modified for my paths. I also included the commands of some system info & dpkg list as posted above.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

More examples:
Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

