---
title: "Move the users home directory to an external drive"
date: 2010-01-19
forum: General Help
---

### Post by jamiepgs on 2010-01-19
Hey

As I regularly move between Mac and PC, I thought it would be a good idea to put all my data on an external drive. As Windows 7 and OS X have similar home folder layouts, I just simply put all the folders I need for both on the root of the external drive and changed a few settings so that the Home folder for my user is on the external drive on both Windows and OS X. 

Whilst Ubuntu also has a similar structure, I cannot work out how to have it so that my users home folder is on the external drive. I have done a little research and all I can find is how to have the /home directory on another partition. a) this is not what I'm trying to do, just the folder for my user and b) this would mean formatting the external drive to extX format, which just wouldn't work for me.

I am using 9.10 (or will be once the upgrade is complete) 

Thanks

---

### Post by audiomick on 2010-01-19
The safest would be to leave /home where it is. A separate partition is a good idea, because you can re-mount it when you re-install fresh, thereby retaining not only your data, but your settings as well.

You can set the default save path for pretty much everything to somewhere else than home, or set up links to another place in home. I don't know how to do the latter, I'm sorry, I've just read about people doing it.

---

### Post by J V on 2010-01-19
My suggestion: Symlinks...

It probably won't automatically load it as home because its smart enough to know that external drives won't *always* be there, and /home is generally supposed to be...

You can create symlinks... Either one big one at ~ leading to the HD, or lots of little ones from Documents > My Documents etc...

---

### Post by Leppie on 2010-01-19
as you are dedicating a whole drive/partition to the /home folder, you don't actually need to create the /home folder itself on the destination drive. the root of that drive will be mounted into the /home folder in the root of your ubuntu filesystem.
what you basically need to do, is copy the contents of your current /home folder to the destination drive. then you need to tell the filesystem that you have a new location for this folder, so you create an entry or if it already exists modify the entry in fstab.
open the fstab with an editor of your choice:
```
sudo gedit /etc/fstab
```then modify/create the /home entry. mine looks like this:
```
UUID=9ce1ca52-d0b3-4314-85ee-f09eaa4dc721    /home    xfs    defaults    0    2

```
then save and exit.
switch to recovery mode:
```
sudo telinit 1
```
in the recovery shell, go to the (old) /home folder:
```
cd /home
```
and backup your things there:
```
mkdir backup
mv * backup/
```
then reboot

---

### Post by bodhi.zazen on 2010-01-19
> **jamiepgs said:**
> Whilst Ubuntu also has a similar structure, I cannot work out how to have it so that my users home folder is on the external drive. I have done a little research and all I can find is how to have the /home directory on another partition. a) this is not what I'm trying to do, just the folder for my user and b) this would mean formatting the external drive to extX format, which just wouldn't work for me.

What you are wanting to do can not be done.

First, from your question, I do not think you do not understand how the Linux file system works. If you have /home on an external HD you would mount it at /home

If you have /home/your_user on an external HD, you would mount it at /home/your_user

This is managed in fstab

This is a set of detailed, step by step directions :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Second you can not use a FAT or NTFS partition for your home directory because those file systems do not use permissions. So even though your can rw to FAT or NTFS, you can not set the required permissions for the various files and directories in your home directory, so , yes you need to use a linux native file system, such as ext3/4 , jfs, etc.

IMO the best solution is to use a a /data partition . You then create links in Ubuntu

ln -s /data/music /home/you/music

and on ...

---

### Post by bodhi.zazen on 2010-01-19
> **Leppie said:**
> as you are dedicating a whole drive/partition to the /home folder, you don't actually need to create the /home folder itself on the destination drive. the root of that drive will be mounted into the /home folder in the root of your ubuntu filesystem.
what you basically need to do, is copy the contents of your current /home folder to the destination drive. then you need to tell the filesystem that you have a new location for this folder, so you create an entry or if it already exists modify the entry in fstab.
open the fstab with an editor of your choice:
```
sudo gedit /etc/fstab
```
then modify/create the /home entry. mine looks like this:
```
UUID=9ce1ca52-d0b3-4314-85ee-f09eaa4dc721    /home    xfs    defaults    0    2

```

The OP wishes to share the partition across multiple OS, so, XFS will not work.

The OP stated ext will not work for him/her either ...

---

### Post by Leppie on 2010-01-19
> **bodhi.zazen said:**
> The OP wishes to share the partition across multiple OS, so, XFS will not work.

The OP stated ext will not work for him/her either ...
i never said the OP has to use xfs, i said that my entry looks like that
actually AFAIK using samba, he could use whatever his ubuntu system supports

---

### Post by jamiepgs on 2010-01-19
Symlinks worked a treat, thanks :)

---

### Post by J V on 2010-01-19
You're welcome (na na nana na :P)

---

### Post by nabilalk on 2010-02-10
> **Leppie said:**
> as you are dedicating a whole drive/partition to the /home folder, you don't actually need to create the /home folder itself on the destination drive. the root of that drive will be mounted into the /home folder in the root of your ubuntu filesystem.
what you basically need to do, is copy the contents of your current /home folder to the destination drive. then you need to tell the filesystem that you have a new location for this folder, so you create an entry or if it already exists modify the entry in fstab.
open the fstab with an editor of your choice:
```
sudo gedit /etc/fstab
```then modify/create the /home entry. mine looks like this:
```
UUID=9ce1ca52-d0b3-4314-85ee-f09eaa4dc721    /home    xfs    defaults    0    2

```
then save and exit.
switch to recovery mode:
```
sudo telinit 1
```
in the recovery shell, go to the (old) /home folder:
```
cd /home
```
and backup your things there:
```
mkdir backup
mv * backup/
```
then reboot

I followed the above instructions without reading the rest of the thread first (my mistake) and now my Home directory is missing and Ubuntu 9.10 will not allow me to login. How can I put the home directory back to where it was originally?

---

