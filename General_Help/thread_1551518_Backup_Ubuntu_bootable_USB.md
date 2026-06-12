---
title: "Backup Ubuntu bootable USB"
date: 2010-08-12
forum: General Help
---

### Post by Peter7K on 2010-08-12
Here is what I would like to pursue:

I would aim to create a USB drive which a system can boot from if needed.  However, this system would not be the generic Lucid 10.04 iso, it would have specific packages that my current system has.  Also, it would start up and run with my current system settings if possible.

I did look into [Reconstructor]("https://build.reconstructor.org/"), but it doesn't appear that that would have the capibility of changing the default settings to match my current system's settings.  Also, it looked like there wasn't a way to upload a list of current packages of my system (I would have to manually select each package, taking quite a while).  

So is there any way to make a bootable USB matching my current system?  Or is reconstructor the closest thing to that kind of customiz-ability?  Thank you for your time!

---

### Post by dabl on 2010-08-12
> **Peter7K said:**
> 

 a USB drive which [COLOR="SeaGreen"]**a system**[/COLOR] can boot from 



Right there is the challenge.  The *buntu kernel is fairly agile in detecting display hardware, audio chip, USB system, etc. etc. but it can't know everything about every system in the world, with no configuration information.

On the other hand, if you said "my system", then it's as simple as doing a normal installation on the hard drive, including installing Grub on it, and then (when you need to boot it) setting your BIOS to boot that device first.  As far as your personal settings are concerned, if you install the same packages on it, then just copy all the "dot" files and folders from your user folder on your main system to the user folder on the external drive, and they should look and work the same.

---

### Post by oldfred on 2010-08-12
You can create a list of installed packages and use that to reinstall all of them. I do this for all my new installs. The first time I used this was from an old install and it reinstalled a lot of old packages I really did not want so it would pay to houseclean first. I run this before backups and copy list into /home so it gets backed up also.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Above list is just the packages, not versions as it will reinstall with the current version.

IF you want a list with extra description of what they are:
List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

If you have made any system wide settings, video, sharing, sources, custom fstab, grub settings, network they will be in /etc. I try to remember everything I change and put a copy into a /home folder so my backups include those settings also as I only really backup /home.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

