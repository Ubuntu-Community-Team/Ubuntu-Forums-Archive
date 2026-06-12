---
title: "Restore to a new (bigger) hard drive"
date: 2011-09-26
forum: General Help
---

### Post by DawgMan on 2011-09-26
I have a Dell Latitude D830 with a 500 GB hard drive.  Currently dual booting with Windows and Ubuntu 10.04.

Like most Ubuntu users I have made many many customizations to my system. I am sold on Ubuntu now and want to get rid of my dual booting system.  I want to keep all my settings licenses etc for things like compiz, awn, vmware workstation, cross over and true crypt to name a few.

So, hard drives being inexpensive, I bought another 500GB hard drive. My thought is to put in the new hard drive and load Ubuntu 10.04.  Then connect my old hard drive with an external USB adapter and copy/restore everything except the Windows drive and the Grub dual boot.  Also, I want to use the full 500GB.  Now I have 400 linux and 100 Windows.  

So the question is: A. will it work? and B. What do I copy or better yet what do I not copy (like fstab etc)?

Dan

---

### Post by wildmanne39 on 2011-09-26
Hi, you could copy your home folder including hidden files to the new drive, you will have to reinstall any applications that are not installed in ubuntu by default but you will have all personal data and configuration settings that you saved to your home folder.

Also you could use clonezilla and make a clone of your ubuntu partition then put it on your new drive, here is a link for that.
[http://www.clonezilla.org/](http://www.clonezilla.org/)
Thank you

---

### Post by stlsaint on 2011-09-26
> **DawgMan said:**
> I have a Dell Latitude D830 with a 500 GB hard drive.  Currently dual booting with Windows and Ubuntu 10.04.

Like most Ubuntu users I have made many many customizations to my system. I am sold on Ubuntu now and want to get rid of my dual booting system.  I want to keep all my settings licenses etc for things like compiz, awn, vmware workstation, cross over and true crypt to name a few.

So, hard drives being inexpensive, I bought another 500GB hard drive. My thought is to put in the new hard drive and load Ubuntu 10.04.  Then connect my old hard drive with an external USB adapter and copy/restore everything except the Windows drive and the Grub dual boot.  Also, I want to use the full 500GB.  Now I have 400 linux and 100 Windows.  

So the question is: A. will it work? and B. What do I copy or better yet what do I not copy (like fstab etc)?

Dan

NOTE: I missed the above poster already mentioning the use of clonezilla. Sorry about double post.

In your case I would use something along the lines of [clonezilla]("http://clonezilla.org/"). Simply clone the partition containing ubuntu. This image will copy your ubuntu install exactly as it is and will place it right back on the new drive the exact way it is now. Unless you are splitting your install across multiple partitions: IE, seperate (/, /home, /boot, etc) I would suggest doing it this way. Can even copy over your swap partition same way or make new one on new drive.

---

### Post by oldfred on 2011-09-26
Nothing really wrong with the copy with clonezilla, but I am more a fan of the clean install. I upgraded in place many times and when I did a clean install I found I had lots of cruft. Most of that I now know I can houseclean but a clean install automatically starts fresh.

My back up strategy is just a clean install and restore my /home. Since you will have old drive anything you forget to copy will still be available to copy. 

Several backups use rsync.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

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
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

Do not copy /etc back, again you may have custom settings but a new install may have some that are different, but you may need your custom settings to be able to copy them into your new /etc. Sources also should not just be copied back, especially if a different version. But again you may want to know what you had added.

The only things not listed above would be apps you installed from .debs or other direct installs.

More info on using dpkg to list installed apps.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by DawgMan on 2011-09-26
Thanks to all.

That's what I needed to know.  I will try a combination of the above.  Since I will have the old drive I can swap back and forth and worst case restore from clonezilla.  I think a clean install would help since, like others, I did a lot of customizing over the years and maybe didn't clean up as much as needed.

---

