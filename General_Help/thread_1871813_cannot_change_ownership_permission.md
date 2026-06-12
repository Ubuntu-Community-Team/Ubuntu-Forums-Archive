---
title: "cannot change ownership permission"
date: 2011-10-29
forum: General Help
---

### Post by alesserfate on 2011-10-29
Hi all,

Using Ubuntu 10.04

I've copied a folder from my local drive NTFS partition to an external USB drive which has an EXT3 partition. After copying the folder I cannot open it from the USB drive because I don't have permission. :(

The USB drive is a part of my NAS and is normally plugged into a linux NAS device which uses linux as its core operating system. 

The share I put my folder in to is under permissions as set in the NAS device, it's one of the users' shares.

How can I use my ubuntu laptop to copy the ownership/permissions of the share and apply it to the folder and all its contents while connected through USB.

I do NOT have terminal / gui access to this NAS box.

Here it is below - I want the FOLDER to have same exact owner/permissions as the sample.

-rwxrw---- 1 2000  501    0 2011-10-29 11:43 sample
drwx------ 9 root root 4096 2011-10-29 02:17 FOLDER


Any help would be greatly appreciated!

---

### Post by alesserfate on 2011-10-29
Was able to solve the problem, since the user/owner was on a different system I couldn't manually reproduce the settings but doing with a reference file is possible.

The 'sample' file I created over the network on the NAS share to ensure appropriate permission settings in it.

Went into terminal as root.

First I copied the permission settings of rwxrw---- to the FOLDER using appropriate chmod -R commands.

Than I used:

chgrp -R --reference=sample FOLDER
chown -R --reference=sample FOLDER

Hope this helps anyone if anyones ever in the same boat.

---

### Post by mörgæs on 2011-10-29
Good, then please mark the thread 'solved'.

---

