---
title: "fstab auto mount not working"
date: 2011-07-16
forum: General Help
---

### Post by doogiekd on 2011-07-16
dear friends, 

i am trying to use fstab to mount an iso file. 

important points:

the iso file is not on a cdrom - it is in a directory on a regular user's account.

i do not want the iso file auto mounted at startup.

i want all users to have the ability to mount the iso file - using a command in each user's startup applications: "mount/path/to/image.iso."

the iso file is located in a regular user's account  - not on the administrator's (superuser) account.

the iso image file is the only file located in directory "isoimages."

the mount point is located in the directory "isomount" and is empty, even when using "show hidden files."

i have tried the following command options in the administrator's account using "sudo gedit /ect/fstab" :

/home/steveq/isoimages/looksee.iso /home/steveq/isomount udf,iso9660 user,noauto,loop 0 0 

/home/steveq/isoimages/looksee.iso /home/steveq/isomount udf,iso9660, user,noauto,loop 0 0 (comma after iso960)

/home/steveq/isoimages/looksee.iso /home/steveq/isomount iso9660 loop,user,noauto 0 0

/home/steveq/isoimages/looksee.iso /home/steveq/isomount iso9660, loop,user,noauto 0 0 (comma after iso9660)

/home/steveq/isoimages/looksee.iso /home/steveq/isomount user,noauto 0 0

/home/steveq/isoimages/looksee.iso /home/steveq/isomount ro,user,noauto 0 0

each of these commands causes an error at reboot and i have to press the "s" key to skip the mounting of looksee.iso. after i do this, it boots normally.

possible causes:

syntax error in the fstab file?

can you make an .iso file on a regular user's account have the ability for all users to mount it - using the fstab file in the root (superuser) fstab file?

any suggestions would help -

thanks, 

k.

---

