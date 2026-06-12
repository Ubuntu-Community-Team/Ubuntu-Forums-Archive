---
title: "looking for a more efficient way to backup my whole system"
date: 2010-05-04
forum: General Help
---

### Post by nerdy_kid on 2010-05-04
up to this point ive been using dd if=disv of=file to backup my systems, but this eats a lot of space that i could use.  is there a better way to use dd to have it only copy the sections of the disk that have data in them?  I have tried remastersys but i need a faster way of doing it, and making a squashfs out of an 180Gb drive takes FOREVER. i dont need compression.

thanks :)

---

### Post by gear.h34d.2012 on 2010-05-04
> **nerdy_kid said:**
> up to this point ive been using dd if=disv of=file to backup my systems, but this eats a lot of space that i could use.  is there a better way to use dd to have it only copy the sections of the disk that have data in them?  I have tried remastersys but i need a faster way of doing it, and making a squashfs out of an 180Gb drive takes FOREVER. i dont need compression.

thanks :)

Post deleted because I didn't read your post all the way through. :-/

---

### Post by Mark Phelps on 2010-05-04
Have you looked into clonezilla? It only copies off the used space.

---

### Post by oldfred on 2010-05-04
I am of a different school of thought. Not for mission critical systems but ok for a home user.

I only back up data and figure if system goes south I plan on a total new install, so why backup system and installed programs? So /home and I have separate /data are important. Some also say system settings in /etc but I try to save the few configs that I have edited in my data directory and also have some notes in my data files on the changes so I do not even back up /etc.

I occassionly export my installed programs to a list in my data directory so I can easily recover everything I installed.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Since I more often want 1 file back I do not want a compressed image but files backed up so I can easily recover just one. So I usually copy important data to DVDs or use rsync to a backup directory.

---

### Post by nerdy_kid on 2010-05-05
> **oldfred said:**
> I am of a different school of thought. Not for mission critical systems but ok for a home user.

I only back up data and figure if system goes south I plan on a total new install, so why backup system and installed programs? So /home and I have separate /data are important. Some also say system settings in /etc but I try to save the few configs that I have edited in my data directory and also have some notes in my data files on the changes so I do not even back up /etc.

I occassionly export my installed programs to a list in my data directory so I can easily recover everything I installed.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Since I more often want 1 file back I do not want a compressed image but files backed up so I can easily recover just one. So I usually copy important data to DVDs or use rsync to a backup directory.

thanks!  will definitely check that out :) 

oh i just discovered that mksquashfs has options to turn off compression :)  thats very nice.  thanks for all your help guys

---

