---
title: "Re-installing Ubuntu on first disc"
date: 2010-08-19
forum: General Help
---

### Post by Quackers on 2010-08-19
I have Ubuntu installed on my second hard drive. I have Vista and Mac OS X installed on my first hard drive. I want to delete the Ubuntu installation on the second hard drive and delete the vista partition on the first hard drive, then re-install Ubuntu where vista was. I have some questions.

For the new Ubuntu installation I plan on creating a 3GB swap partition, a 17GB / partition and a 120GB /Home partition.
Does it matter what order I create the partitions in? 

Secondly in order to get all my current settings/programs installed on my new installation I intend to backup my current Home partition to transfer later. Is that enough or would I need to backup etc, usr, var files or more?

Does anybody have a link to the commands I would need to use to transfer the home, etc, usr, var files?
I have read some threads on the subject but, to be honest, they don't appear to agree with each other :-?

Thank you

---

### Post by dagdeniz on 2010-08-19
I don't think that you'll need anything other than /home. They won't be useful. 

The order of the partitions is not important. For a neat backing up of your files in /home, you can prepare the 120 gigs partition and move them before you re-install ubuntu to the other drive. A tutorial of moving your home partition is described here:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Quackers on 2010-08-19
Thanks for that dagdeniz. I was going to backup /home to dvd, but yours is a better way. (I'm having problems getting a dvd to mount in order to delete its contents - it plays dc's and dvd's no problem, but when I put in a used data dvd it won't mount, so I can't delete the contents).

---

### Post by oldfred on 2010-08-19
You can also make a list of installed apps. It is just a list of apps and will reinstall with the more current version if upgrading.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

You may have some settings that are system wide in /etc, but I do not like to just copy them as new versions may have totally different settings. But if you have customized grub, video, or networking you may want to copy your current config files.

---

### Post by Quackers on 2010-08-19
Thanks oldfed. That may come in very handy.

---

### Post by Quackers on 2010-08-19
I now have an old Ubuntu installation on /dev/sdb1 and a new installation on /dev/sda
I want to copy the home folder from the old install to the new /home partition on the new drive (/dev/sda4).

All the guides that I have looked at assume that you are moving the home folder to a new location within the same install.
I am not.
I want to move the old /home to the new /home partition of the new install, so I can transfer settings from the old install to the new. I want it to mount it automatically when the new install is booted. 
I don't want to delete the old home folder as I will have the 2 installations running side by side for a while.

Can somebody point me in the right direction please?
Thanks

---

### Post by oldfred on 2010-08-19
It should not be any different. Did you include the new /home as part of your install so it is already mounted? If so just mount your oldhome and copy. If not your will have to also edit fstab.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

---

### Post by Quackers on 2010-08-19
Hello oldfred, sorry I've been busy :-)
I am now booted into the new installation. The new installation has /home on a seperate partition. It is mounted ok. I can mount the old /home folder with Places > Computer > FileSystem(on other disc) but don't know how to copy the old to the new as they are in different systems.

BTW, the installed apps thing worked well :-)

---

### Post by oldfred on 2010-08-19
If you have clicked on your old home it may be mounted under /media/??. I might unmount and manually mount

$sudo mkdir /mnt/oldhome
$sudo mount -t ext3 /dev/???  /mnt/oldhome

cd /mnt/oldhome/home/
That should be your full old home, be sure to include the extra /home or you may copy the entire system
ls   #should show your old home 

sudo cp -ax * [FONT=Verdana]/home[/FONT]

I am guessing on some of the command as I cannot see exactly how you have mounted. I ofter have to add or delete a trailing / as I am no expert on cp command. I end up with all my data one level up or down depending and then have to delelte & rerun. If you have lots of data you can test by just copying one directory but then you have to include the extra path on both sides of command.

[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

### Post by Quackers on 2010-08-19
Thanks for all your efforts oldfred.
In the end I just got them side by side on my desktop and copy/pasted the missing files (and hidden ones too). 
Obviously I will be picking up the pieces for a while :-). Some things worked right away, like Conky and ConkyForecast, but others don't, like GoogleEarth. Cheese doesn't pick up my webcam any more (although it did when I was on /dev/sdb).
I'll go rooting around and see what I can fix.

---

### Post by oldfred on 2010-08-19
Something like webcam may have been a system setting not a user setting. System settings will be in /etc. But I do not know where to look in /etc for webcam settings.

---

### Post by Quackers on 2010-08-19
It's very odd that it worked on /dev/sdb install right out of the box. But it didn't work on /dev/sda the first time I installed Lucid, and it doesn't work now. That can't be any more than a coincidence, surely.
Everything else is fine now. I uninstalled and re-installed Google Earth and Cairo Dock and they're both good now :-)

---

