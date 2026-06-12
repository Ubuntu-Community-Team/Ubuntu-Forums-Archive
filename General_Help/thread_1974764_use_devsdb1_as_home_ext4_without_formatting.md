---
title: "use /dev/sdb1 as /home ext4 without formatting?"
date: 2012-05-06
forum: General Help
---

### Post by gypsumwolf on 2012-05-06
I have 2 hard drives. Drive one is for the linux install, drive 2 already is ext4 with files on it, but never was used as /home. 

During a fresh reinstall (using the standard graphical installer) I want to tell the installer to use the second drive as ext4 for /home (WITHOUT FORMATTING).
When I do, will it destroy any data or just add all the /home/* directories to it?
-If there is already a folder called downloads, will it destroy that directory or just use that dir since its there?

---

### Post by oldfred on 2012-05-06
Interesting question and I do not know.  But another alternative.

But I leave /home inside my / (root) and mount my data partition in /mnt/data and link all the folders into my /home replacing Music, Video etc. Then my /home only has the user settings in hidden files & folders. And any program that starts to write a lot of data in hidden folders, like Firefox & Thunderbird also get moved to a data partition.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Bandit on 2012-05-06
Easy as pie.
First make sure you can access the drive and it is set to mount at boot. See your mtab and fstab files to verify everything is good to go.
Then just create a /home folder and move everything over to that drive. 
Verify everything did move and all your permissions are set for your username for your folder.
Then simply as root remove the /home folder and create a symlink from / to /home on the other drive.

At least thats how I do it if I dont create seperate ones at install.

---

### Post by xyzzyman on 2012-05-06
You just have to choose the option to manually configure partitions while doing a clean install, and choose ext4 as the partition type and make sure that 'format partition' is NOT checked, and set it to mount as /home. It'll create directories in their for your user accounts at the top level, and not touch your other directories. They will be available under /home though (You may need to change permissions though afterwards to access them).

---

