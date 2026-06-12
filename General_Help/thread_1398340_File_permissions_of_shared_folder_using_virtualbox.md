---
title: "File permissions of shared folder using virtualbox"
date: 2010-02-04
forum: General Help
---

### Post by nikwasi on 2010-02-04
I am running ubuntu using VirtualBox on a Macbook Pro. I wanted to share my documents folder on the Mac in the virtual machine. I had no issues creating/mounting  the share folder on ubuntu. However the file permissions for the shared folder are owned by root. 
```
 
drwx------  1 root     root        1088 2010-02-04 10:18 Mac_Share/

```I used the following command to mount the folder: 
```
sudo mount -t vboxsf Share_Documents ~/Mac_Share/
```I checked that the folder is mounted I can see what is there using 
```
 sudo ls Mac_Share/
```How do I make the folder accessible to the user? Is there another -option needed to do this in the mount command?  
Or do I need to chown for the directory? If so how to do this?

---

### Post by fiestytom on 2010-02-04
this may be mac related, so you might not find much help here

I have windows XP as a guest on a Ubuntu host, and i got shared folders to work pretty well

sry, I can't help you because i don't use MACS :(

---

### Post by nikwasi on 2010-02-04
I don't think this is a mac issue. 
As I said earlier I can see the files on Ubuntu, however they are owned by root. I would like to be able to access them without sudo commands.

---

### Post by fiestytom on 2010-02-04
have you tried going to:

System > Administration > Users and Groups

try looking for a permission having to do with what you want to do, and add your user to it

---

### Post by nikwasi on 2010-02-04
There aren't any option that help in System > Administration > Users and Groups

I would like to change the owner of the directory from root to a user. 
Running commands as root such as: 

chmod 775 Mac_Share
does nothing, permissions for folder are still ( drwx------  1 root     root )    

chmod -R 775 Mac_Share 
changes the permissions of the files in the directory but not the directory itself. No use if I can't read directory.

---

### Post by fiestytom on 2010-02-04
are you sure there isn't something in there?

Users and groups is a very powerful tool

I had to be in a certain group to access windows (samba) shares in vbox

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145976&stc=1&d=1265306801[/IMG]

I don't know what MACS use for file-sharing

---

### Post by SecretCode on 2010-02-04
What's the filesystem of the host shared documents folder? 

You should look at the mount options rw and (if the filesystem doesn't have user/group/other permission bits) umask.
Something like
```
sudo mount -t vboxsf Share_Documents ~/Mac_Share/ -o rw,umask=0000
```

Or, define the share in /etc/fstab with the user or users options, and then mount them without sudo.
Add a line like 
```
Share_Documents	/media/Mac_Share	vboxsf	rw,users,umask=0000	0	0
```

Not tested and not guaranteed!

---

### Post by nikwasi on 2010-02-04
Thanks SecretCode,
I researched mount option more closely and found a solution. 

I googled some more on the subject: "virtualbox mount shared folder from mac host to linux guest"  and found a useful link:  [http://davidherron.com/node/1043](http://davidherron.com/node/1043)

Here David Herron walked through how he setup the mount including the issue I am having with root. 

I was able to read the file by defining uid and gid with the -o option for mount 
```
sudo mount -t vboxsf -o uid=1000,gid=1000 Share_Documents ~/Mac_Share/
```

I can now read/write  the files as local user. 

Thanks everyone for their help, 
- nikwasi

---

### Post by SecretCode on 2010-02-04
Great. (You can mark the thread as solved now.)

---

### Post by BBirdtree on 2010-02-06
Same happened to me (mac os host, ubuntu guest). My solution was to share another folder in virtualbox (i used the mac /Users/Shared) and the mounting in ubuntu sudo mount -t vboxsf shared /home/(mountpoint). worked.

---

### Post by chientai on 2012-01-18
Thanks SecretCode. I can user shared folder on mac host, ubuntu guest now!

---

