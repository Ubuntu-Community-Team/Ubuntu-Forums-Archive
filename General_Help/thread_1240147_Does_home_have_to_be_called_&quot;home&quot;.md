---
title: "Does /home have to be called &quot;/home&quot;?"
date: 2009-08-14
forum: General Help
---

### Post by CoreyB. on 2009-08-14
Down the road I am thinking about creating a separate partition with my home directory on it.  I was wondering if the home directory has to be called home?  Can I have a setup that has the root of the partition as my "home folder"?

---

### Post by squaregoldfish on 2009-08-14
If you have a separate partition, it has to be mounted as a directory somewhere under /, so it's readable in the filesystem. Consequently, you can simply mount your new partition as /home, and you've got what you want.

Steve.

---

### Post by aysiu on 2009-08-14
You have to mount it as /home if you want it to function as home (i.e., contain user settings and files).

After that, you can always create a symlink to it called /home folder if you like: ```
sudo ln -s /home /home\ folder
```

---

### Post by Cheesemill on 2009-08-14
> **aysiu said:**
> You have to mount it as /home if you want it to function as home (i.e., contain user settings and files).
 
You don't have to, the home folder can be anywhere you want. It's set per user in the passwd file.
 
If you do:
```
sudo vipw
```
 
You can edit the location of your home folder. For example my entry in the passwd file is:
```
 rob:x:1000:1000:Rob Pinder,,,:[COLOR=red]/home/rob[/COLOR]:/bin/bash
```

---

### Post by CoreyB. on 2009-08-14
Ok, so right now I have a partition that is located at "/media/OS".  So is it possible to somehow tell Ubuntu that I want to use "/media/OS" as my home directory so if, for example, if I wanted to access my music the path would be "/media/OS/Music"?

Thanks for the help so far! (pretend I clicked the "Thanks" button that used to be on the forum for the above posters :))

---

### Post by aysiu on 2009-08-14
> **Cheesemill said:**
> You don't have to, the home folder can be anywhere you want. It's set per user in the passwd file.
 
If you do:
```
sudo vipw
```
 
You can edit the location of your home folder. For example my entry in the passwd file is:
```
 rob:x:1000:1000:Rob Pinder,,,:[COLOR=red]/home/rob[/COLOR]:/bin/bash
``` I stand corrected. Symlinking isn't the only way to do it, then.

I still would recommend it over manually editing the /etc/passwd file, though. Some programs may by default go looking for things in /home/*username* or try to place things in there by default. Also, any time you add a new user, you'd have to manually change the /etc/passwd file for that user and move all her files and folders to the new location.

I think a symlink is a cleaner way to do it. I previously thought it was the only way. Now I know better.

> **CoreyB. said:**
> Ok, so right now I have a partition that is located at "/media/OS".  So is it possible to somehow tell Ubuntu that I want to use "/media/OS" as my home directory so if, for example, if I wanted to access my music the path would be "/media/OS/Music"? If you used a live CD to copy all your files to /media/OS and then did either the /etc/passwd fix or the symlink, then, yes, you could.

For instructions on that process, go here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dcstar on 2009-08-14
> **CoreyB. said:**
> Ok, so right now I have a partition that is located at "/media/OS".  So is it possible to somehow tell Ubuntu that I want to use "/media/OS" as my home directory so if, for example, if I wanted to access my music the path would be "/media/OS/Music"?


Woah - any "/home" folder **must** be on a filesystem that fully supports all Linux security requirements.

Many people uses Windows filesystems for their media and these **cannot** be used for /home purposes.

---

### Post by aysiu on 2009-08-14
> **dcstar said:**
> Woah - any "/home" folder **must** be on a filesystem that fully supports all Linux security requirements.

Many people uses Windows filesystems for their media and these **cannot** be used for /home purposes.
You're correct, but couldn't /media/OS be formatted as Ext3 and not FAT32 or NTFS?

---

### Post by CoreyB. on 2009-08-14
> **dcstar said:**
> Woah - any "/home" folder **must** be on a filesystem that fully supports all Linux security requirements.

Many people uses Windows filesystems for their media and these **cannot** be used for /home purposes.

Oh, I didn't know that.  I was thinking about buying a Macbook down the road and I thought it would be ideal to have all of the "home" directories for OSX, Windows, and Ubuntu to go to the same location on a separate partition.  NTFS is the only filesystem I know that can be read by all of these systems.

Am I missing any filesystems that would work for this?

---

### Post by hibliss on 2009-08-14
EXT2 can be read by all three with additional drivers I believe.

---

### Post by ad_267 on 2009-08-14
The home partition is also used to store all your program configurations in hidden files and directories. It would be a better idea to have a normal /home for Ubuntu, and a shared /data directory that you could symlink too from inside your home directory. That data partition could be any file system.

---

### Post by aysiu on 2009-08-14
> **ad_267 said:**
> The home partition is also used to store all your program configurations in hidden files and directories. It would be a better idea to have a normal /home for Ubuntu, and a shared /data directory that you could symlink too from inside your home directory. That data partition could be any file system.
This is a good plan. And it should be FAT32, not NTFS. As far as I know, Mac OS X can't work with NTFS natively (maybe there's some kind of hack plugin that will allow it).

---

### Post by ad_267 on 2009-08-14
Yeah I should clarify that when I said "any file system", I meant as far as Ubuntu is concerned, as long as it can read it. So not really any file system. :)

---

### Post by CoreyB. on 2009-08-15
Ok, all I really want is to have a common Documents, Video, and Pictures directories that can be read by all of the operating systems.  Would it be possible to keep my home directory with Ubuntu, but use symlinks so that if I click Documents from the gnome menu, it goes to a Documents folder on a separate partition?

---

### Post by michy99 on 2009-08-15
Definitely, and probably the best solution.

---

