---
title: "setup xbmc for guest user?"
date: 2012-06-09
forum: General Help
---

### Post by qwertyjjj on 2012-06-09
I have xbmc installed under my login.
How can I create a new guest login which does not have access to any of my thunderbird or mozilla profiles but runs the current install of xbmc including all the library files inside it?

---

### Post by Jose Catre-Vandis on 2012-06-09
Create new user and give that user permission to view media files (or move media files to a shared location out of "your" home)

---

### Post by qwertyjjj on 2012-06-09
> **Jose Catre-Vandis said:**
> Create new user and give that user permission to view media files (or move media files to a shared location out of "your" home)

So, I have to move all media files outside of home and then get xbmc to rerun the library import?

Where do I move them to? /root/media?
How do I give permission to those files? Just make them all 777?

---

### Post by Jose Catre-Vandis on 2012-06-09
Yes, or give your guest user read permissions to your home media files.

777 gives read/write to you guest, so you might want to restrict slightly using 644 or similar

---

### Post by papibe on 2012-06-09
Hi qwertyjjj.

You need 2 things:
[LIST]
[*]Give read access to the media files, and
[*]Either rescan the library, or (better) copy/sync the XBMC thumbnails and database.
[/LIST]
If you are concern about privacy, one simple solution would be to remove the execute permission to your home directory so other users:
[LIST]
[*]can't 'cd' or browse into it, and
[*]can only can access files from within knowing its name and path.
[/LIST]
This would take care of that:
```
chmod 744 /home/youruser
```

To avoid rescanning the library, you can copy the ~/.xbmc directory:
```
sudo rsync -av ~youruser/.xbmc/  ~newuser/.xbmc/

sudo chown -R newuser:newuser ~newuser/.xbmc/
``` 

I hope that helps, and tell us how it goes.
Regards.

EDIT 1: The XBMC database contains the filename and paths to your media, so the newuser will be able to have access to them.

EDIT 2: If you find yourself to be in a situation where you need to keep sharing your media more, and more (family members, room-mates, etc), it would be a good idea to move the media outside your home directory. That way you would increase privacy to your personal files, and make it easy for other people to have access to it.

---

### Post by qwertyjjj on 2012-06-10
> **papibe said:**
> Hi qwertyjjj.

You need 2 things:
[LIST]
[*]Give read access to the media files, and
[*]Either rescan the library, or (better) copy/sync the XBMC thumbnails and database.
[/LIST]
If you are concern about privacy, one simple solution would be to remove the execute permission to your home directory so other users:
[LIST]
[*]can't 'cd' or browse into it, and
[*]can only can access files from within knowing its name and path.
[/LIST]
This would take care of that:
```
chmod 744 /home/youruser
```

To avoid rescanning the library, you can copy the ~/.xbmc directory:
```
sudo rsync -av ~youruser/.xbmc/  ~newuser/.xbmc/

sudo chown -R newuser:newuser ~newuser/.xbmc/
``` 

I hope that helps, and tell us how it goes.
Regards.

EDIT 1: The XBMC database contains the filename and paths to your media, so the newuser will be able to have access to them.

EDIT 2: If you find yourself to be in a situation where you need to keep sharing your media more, and more (family members, room-mates, etc), it would be a good idea to move the media outside your home directory. That way you would increase privacy to your personal files, and make it easy for other people to have access to it.

With this process, would I need to rerun rsync everytime I add a new file to the library?
Also, if I move all the files outside of my home folder, do I need to rerun the import in xbmc or is there a way I can change the media locations?

VirtualBox VMs/
rsync: chgrp "/home/j-media-centre/mnt/VirtualBox VMs" failed: Operation not permitted (1)
VirtualBox VMs/aaa/
rsync: failed to set times on "/home/j-media-centre/mnt/VirtualBox VMs/aaa": Operation not permitted (1)
VirtualBox VMs/aaa/aaa.vbox
VirtualBox VMs/aaa/aaa.vbox-prev
VirtualBox VMs/aaa/bbb XP.vdi

---

### Post by Jose Catre-Vandis on 2012-06-10
Where does Virtualbox come into it? You just added another potential layer of complexity :)

---

### Post by papibe on 2012-06-10
> **qwertyjjj said:**
> With this process, would I need to rerun rsync everytime I add a new file to the library?
Yes, because the new user can't scan your directory.

> **qwertyjjj said:**
> Also, if I move all the files outside of my home folder, do I need to rerun the import in xbmc or is there a way I can change the media locations?
There are a couple of ways. However, neither one is very simple. You can export/import your database, or run directly some sql commands to fix it.

> **qwertyjjj said:**
> VirtualBox VMs/
rsync: chgrp "/home/j-media-centre/mnt/VirtualBox VMs" failed: Operation not permitted (1)
VirtualBox VMs/aaa/
rsync: failed to set times on "/home/j-media-centre/mnt/VirtualBox VMs/aaa": Operation not permitted (1)
VirtualBox VMs/aaa/aaa.vbox
VirtualBox VMs/aaa/aaa.vbox-prev
VirtualBox VMs/aaa/bbb XP.vdi
This is not related to your current concern. My guess is that there is a problem with the rsync command and you are syncing more data that required. If that's giving you trouble, you can use 'cp' instead.

For instance, logged as newuser:
```
cp -pr  ~youruser/.xbmc  ~/
```
Tell us how it goes.
Regards.

---

### Post by qwertyjjj on 2012-06-10
> **papibe said:**
> Yes, because the new user can't scan your directory.


There are a couple of ways. However, neither one is very simple. You can export/import your database, or run directly some sql commands to fix it.


This is not related to your current concern. My guess is that there is a problem with the rsync command and you are syncing more data that required. If that's giving you trouble, you can use 'cp' instead.

For instance, logged as newuser:
```
cp -pr  ~youruser/.xbmc  ~/
```
Tell us how it goes.
Regards.



That was only one section of the problem. There were lots of other rsync errors.
eg
/usr/share/ca-certificates/mozilla/Visa_eCommerce_Root.crt" failed: Permission denied (13)
rsync: symlink "/home/j-media-centre/mnt/ssl/certs/WellsSecure_Public_Root_Certificate_Authority.pem" -> "/usr/share/ca-certificates/mozilla/WellsSecure_Public_Root_Certificate_Authority.crt" failed: Permission denied (13)
rsync: symlink "/home/j-media-centre/mnt/ssl/certs/Wells_Fargo_Root_CA.pem" -> "/usr/share/ca-certificates/mozilla/Wells_Fargo_Root_CA.crt" failed: Permission denied (13)
rsync: symlink "/home/j-media-centre/mnt/ssl/certs/XRamp_Global_CA_Root.pem" -> "/usr/share/ca-certificates/mozilla/XRamp_Global_CA_Root.crt" failed: Permission denied (13)
ssl/certs/a0bc6fbb.0

---

### Post by papibe on 2012-06-10
I'm very confused since both of your errors from posts #6 and #9 are from things that are outside the xbmc directory. 

Why are you trying to copy those files?
Could you post the command that is giving you those errors?

Regards.

---

### Post by qwertyjjj on 2012-06-11
> **papibe said:**
> I'm very confused since both of your errors from posts #6 and #9 are from things that are outside the xbmc directory. 

Why are you trying to copy those files?
Could you post the command that is giving you those errors?

Regards.

Sorry...think I got mixed up between posts.
This seemed to work and then changing owenership to the new user.
j-media-centre@jmediacentre-A880G:~$ sudo cp -pr  ~j-media-centre/.xbmc  ~movies_music/.xbmc

sudo chown -R movies_music:movies_music /home/movies_music

---

### Post by papibe on 2012-06-11
:D Great!

Now try using XBMC on the newuser, and tell us how it goes.

Regards.

---

### Post by qwertyjjj on 2012-06-25
Nope, doesn't seem to work. xbmc says it can't find the files so maybe it's a permissions error.
Maybe it's best if I move the files to above the /home directory so all users can access the files?
Do the folders need to be on 777?

---

### Post by qwertyjjj on 2012-06-28
Any ideas?
Can I just caopy ~/Videos and ~/Music to something like /myfiles and make everything 777 then instruct xbmc to look there for the library?

---

### Post by qwertyjjj on 2012-06-30
> **papibe said:**
> Hi qwertyjjj.

You need 2 things:
[LIST]
[*]Give read access to the media files, and
[*]Either rescan the library, or (better) copy/sync the XBMC thumbnails and database.
[/LIST]
If you are concern about privacy, one simple solution would be to remove the execute permission to your home directory so other users:
[LIST]
[*]can't 'cd' or browse into it, and
[*]can only can access files from within knowing its name and path.
[/LIST]
This would take care of that:
```
chmod 744 /home/youruser
```

To avoid rescanning the library, you can copy the ~/.xbmc directory:
```
sudo rsync -av ~youruser/.xbmc/  ~newuser/.xbmc/

sudo chown -R newuser:newuser ~newuser/.xbmc/
``` 

I hope that helps, and tell us how it goes.
Regards.

EDIT 1: The XBMC database contains the filename and paths to your media, so the newuser will be able to have access to them.

EDIT 2: If you find yourself to be in a situation where you need to keep sharing your media more, and more (family members, room-mates, etc), it would be a good idea to move the media outside your home directory. That way you would increase privacy to your personal files, and make it easy for other people to have access to it.

I did this but when trying to add a source in xbmc, it cannot see any of the contents of /home/user1

---

### Post by qwertyjjj on 2012-07-04
Wha folder should I move Music and Videos to if moving above the /home folder and also what permissions do I need to give them so that they are acessible y every user?
Also, is there a way to add symlinks to the /home/user1 and /home/user2 folders?

---

