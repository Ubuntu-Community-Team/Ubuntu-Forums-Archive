---
title: "Assistance with permissions"
date: 2010-09-18
forum: General Help
---

### Post by dctalk37 on 2010-09-18
Hello All and thanks to anyone who helps. I'm trying to get a game to work, the mac/wine client for Fallen earth. After reading a few things i was able to download the fallen earth dmg file (named fm.dmg now) and converted it to a img file (fm.img) using dmg2img. Then i mounted it using these commands. 

neon@neon-laptop:~/Downloads$ sudo mkdir /media/mount 
neon@neon-laptop:~/Downloads$ sudo modprobe hfsplus 
neon@neon-laptop:~/Downloads$ sudo mount -t hfsplus -o loop fm.img /media/mount 

I thought i was done. But it seems i cant copy the main file FEUpdaterMac.exe becasue i dont have permisssions. Tried and got the following 

neon@neon-laptop:/media/mount/FallenEarth$ sudo chmod +rwx FEUpdaterMac.exe 
chmod: changing permissions of `FEUpdaterMac.exe': Read-only file system 

Now I'm stuck is there anything anyone can think of everything else seemed to copy but this file. Thanks again for any help.

---

### Post by Lateralis on 2010-09-18
The problem would appear to be that the file system is being mounted in read-only mode.  Possibly want to add the rw option to make the file system read-write.

---

### Post by crackbuntu on 2010-09-18
i came across the same problem some days ago :) do one thing

before u command the terminal to do something, type : sudo su and then enter your sudo (login) password when asked for

then enter the remaining commands :) this will work

regards
from a remote hill in the himalayas :)
temperature : -(minus)29

---

### Post by Lateralis on 2010-09-18
First, a health warning to the above advice.  That will open up a root shell.  Any command you run will be run as root.  Ensure that you take proper security precautions so that your system isn't comprimised. 

Secondly...

> chmod: changing permissions of `FEUpdaterMac.exe':** Read-only file system** 

If the problem was with permissions, I think it would say "Permission denied" here, as opposed to Read-only file system.  So, again, I think the file system needs to be remounted with the rw option.

---

### Post by WorMzy on 2010-09-18
Don't use sudo su. If anything, use sudo -i.

Try mounting with this:

```
sudo mount -t hfsplus -o loop,rw,uid=1000,gid=1000,umask=002 fm.img /media/mount
```

rw = read+write
uid = your UserID
gid = your GroupID
umask = sets the permissions used on the files to 775 (owner: rwx, group: rwx, other: r-x)

---

### Post by dctalk37 on 2010-09-18
Thanks for the help guys. So i did both options presented. Used sudo su then typed my commnad. and the other option trying to change the mount to get rw. I got my mount to come up both times. But when i try to copy the contents to another folder on my pc i get. All the other files will copy.

Error while copying "FEUpdaterMac.exe".
There was an error copying the file into /home/neon/Downloads/FM/FallenEarth.
(expand) Show more Details
Error opening file: Permission denied

---

