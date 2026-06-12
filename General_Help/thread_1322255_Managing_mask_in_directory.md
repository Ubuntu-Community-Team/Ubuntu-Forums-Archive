---
title: "Managing mask in directory"
date: 2009-11-10
forum: General Help
---

### Post by Inixi on 2009-11-10
Hello there,
I have installed vsftpd on my Ubuntu and some users are using this type of file exchanging. In vsftpd there is a jail method, so noone can exit from his/her home directory. I created another directory in which users who belong to special group can save their files and the structure looks like this:

home
- usera
- userb
- shared <-this is the directory where users can save files

I mounted "shared" directory as a directory of other users, and fstab looks like this:
/home/shared  /home/usera/Shared      defaults,bind 0       0
/home/shared  /home/userb/Shared      defaults,bind 0       0

I tried to use symlinks, but vsftpd treated symlink as a file, so the directory could not be read.

The problem is, how to set a mask to this mounted points which would work like that:
usera, who belongs to group let's say "sharedfiles", is coping his file to ~/Shared directory, after copy file gets permissions 770 and owning group would be "sharedfiles, then userb who also belongs to group "sharedfiles" wants to copy this file from ~/Shared directory to his home.
Is there a mothod for that?

---

