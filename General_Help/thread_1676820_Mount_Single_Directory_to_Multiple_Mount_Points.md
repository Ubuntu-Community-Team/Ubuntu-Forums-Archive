---
title: "Mount Single Directory to Multiple Mount Points"
date: 2011-01-27
forum: General Help
---

### Post by sddt on 2011-01-27
Hello, I have a requirement that seems to be unique in nature. I have multiple clients who are caged to their home directories. I would like to "share" a directory which exists above these chroots with all these caged users. I know this can be accomplished using mounts but my problem is, how can I mount a single directory to multiple mount points located in each users home dir? Can this be done in the fstab file? Thank you for any help or suggestions on how to accomplish this.

---

### Post by Zill on 2011-01-27
sddt:  I suggest you take a look at [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by sddt on 2011-01-27
Not sure how that helps me get a Mount Point in each users' home dir. Could you elaborate?

---

### Post by Rocket2DMn on 2011-01-27
Will it work if you mount it in one place and create symlinks in each user's home directory?

---

### Post by sddt on 2011-01-27
I would love to use symlinks but these users are caged to their home dirs respectively. To my knowledge, a symlink will not work if its linked to something outside of a chroot. Here is the folder structure:

```
CompanyRoot
   -Clients
      -Client1 (caged chroot)
         -Inbox
         -Outbox
         -FilesToShareWithCagedUsers (Mount Point)
      -Client2 (caged chroot)
         -Inbox
         -Outbox
         -FilesToShareWithCagedUsers (Mount Point)
      -Client3 (caged chroot)
         -Inbox
         -Outbox
         -FilesToShareWithCagedUsers (Mount Point)
   -OfficeUseFolder
   -FilesToShareWithCagedUsers
   -...

```

Now, if this folder I want mounted in each Clients home dir wasn't so large I would simply make a copy of it in each home dir. The problem is, over time we may have several hundred of these caged Clients. The reason they need to be caged to their own home dir is because I don't want them to be aware of our other clients, hence no access to the parent directory "Clients".

---

### Post by ajgreeny on 2011-01-27
It is certainly possible to have multiple mount points within a single users home, as well as in the file system of the OS where those homes reside, and mount a single partition or folder more than once simultaneously, eg it can be mounted in /media and in /home/user/mountpoint and /home/user2/mountpoint, or I think it can, but I do not have more than one user to test that part of the question you ask.

There is definitely no problem in having several mountpoints in the same home/user as I have just tried it to find out.  If more than one user was editing the same file at the same time, however, I have no idea what would happen.

As to the possibility of multiple lines in fstab to mount the folder in several client's homes at the same time, I suggest you try it.  If it stops the system booting (unlikely to say the least) you can always use a live CD to remove the bad lines, and reboot.

---

### Post by sddt on 2011-01-27
Yes! That second part is my issue. One folder with mountpoints in each user home dir. The problem I have with the fstab approach is, I would have to add a line for each user. This could be cumbersome when considering there could be several hundred such users. Is there a one line entry I could make that would create the mountpoint in all folders eg:

Clients/* /path/to/shared/folder 0 0

I know however the * syntax does not work in fstab by learning the hard way after a reboot. The mount failed which caused the system to hang and would not allow for remote ssh access. Luckily, one of the employees there had a usb keyboard to plug in and press the "s" key for me to get back in. mount -a is a way to test this without having to reboot and lose remote access...

---

### Post by oldfred on 2011-01-27
I saved these links in case I ever needed them:

Shared users using bindfs:
[http://ubuntuforums.org/showpost.php?p=8983087&postcount=25](http://ubuntuforums.org/showpost.php?p=8983087&postcount=25)
HowTo: Create shared directory for local users (with bindfs). 
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by sddt on 2011-01-27
But how would you make that work for users who are caged to their own home dirs? What you've posted seems to relate to users who all have access to the same home/media folder...

I'm trying to avoid the many entries in fstab that would be required to do what I am trying to accomplish.

---

### Post by Zill on 2011-01-28
> **sddt said:**
> Not sure how that helps me get a Mount Point in each users' home dir. Could you elaborate?
A single mount point is on the root directory, not multiple mount points in each home directory.  You just need a single entry in the fstab eg.
```
server:/shareddir /mnt/shareddir nfs rsize=8192,wsize=8192,nosuid,soft 0 0
```
Then add a simlink from /mnt/shareddir to each user's home.  With the right permissions, each user should be able to work with files in the shared directory without access to any other users.

---

### Post by anglican on 2011-01-28
> **sddt said:**
> Hello, I have a requirement that seems to be unique in nature. I have multiple clients who are caged to their home directories. I would like to "share" a directory which exists above these chroots with all these caged users. I know this can be accomplished using mounts but my problem is, how can I mount a single directory to multiple mount points located in each users home dir? Can this be done in the fstab file? Thank you for any help or suggestions on how to accomplish this.I would have thought a series of entries in /etc/fstab, something like:
```
/mnt/shared_directory        /home/caged_user1/mount_point    none    ro,bind 0 0
/mnt/shared_directory        /home/caged_user2/mount_point    none    ro,bind 0 0
```would do what you want.

Oh, I've just noticed that you don't want a huge fstab... so use the mount command instead i.e.

```
mount /mnt/shared_directory /home/caged_user1/mount_point -t none -o ro,bind
```

which you can then put into a shell script to iterate over all your caged users. Something like:
```
#!/bin/bash

for name in /home/caged_user*
do
mount /mnt/shared_directory $name/mount_point -t none -o ro,bind
done
```
fstab doesn't understand globbing - there's no way you could do this in fstab without having all the individual lines.

H

---

### Post by sddt on 2011-01-29
Would this be a script I should have run at startup to ensure the mounts persist after reboot? Thanks for the tip, I figured I would have to get into some bash scripting...

---

### Post by anglican on 2011-01-30
> **sddt said:**
> Would this be a script I should have run at startup to ensure the mounts persist after reboot? Thanks for the tip, I figured I would have to get into some bash scripting...Yes, you would need to run this at startup to ensure mounts persist after reboot. Take a look at ```
man update-rc.d
``` for how to do this. Have you tested that this solution actually works for your caged users - I've not used it in that context but would expect it to work (but lots of things I expect to work don't!).

H

---

### Post by sddt on 2011-01-31
Wow, thank you so much for the info! To answer your question, yes, this solution does work when I run the mount command manually. Thanks again for the tip!

---

