---
title: "question about saving files under the / partition"
date: 2011-01-28
forum: General Help
---

### Post by hunterkasy on 2011-01-28
I have a hhd drive that is dying, and I don't have any money to buy a new one right now,  I am wondering if I can save files from my failing hhd under the / partition, I have filled up my home partition, and I have allot of free space on the / partition

right now I can't because I don't have the proper permission to do so, and I don't know how to make it my self

thanks in advance for any help

---

### Post by mrhhug on 2011-01-28
heres a really basic picture of a linux filesystem

[http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg](http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg)

if your hard drive is failing moving data to a different place on the drive wont help

if you can't copy something because of a permission setting, and easy way to graphically do that is to open a terminal and type
```
gksudo nautilus
```
now you should be able to do anything you want to any file on your system. this is using nautilus as root so you could harm your system. be careful

---

### Post by sisco311 on 2011-01-28
Only root can write to /. So, you have to create a new directory as root and change its owner to your user. You can do it via the GUI by launching the file manager as root:
```
gksu nautilus
```
or via the terminal:
```
sudo mkdir /backup
sudo chown **username**: /backup
```

Where **/backup** is the name of the new directory and **username:** is your login name followed by a colon.

Either way, be very careful!

---

### Post by hunterkasy on 2011-01-29
> **mrhhug said:**
> heres a really basic picture of a linux filesystem

[http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg](http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg)

if your hard drive is failing moving data to a different place on the drive wont help

if you can't copy something because of a permission setting, and easy way to graphically do that is to open a terminal and type
```
gksudo nautilus
```
now you should be able to do anything you want to any file on your system. this is using nautilus as root so you could harm your system. be careful

I guess I should have explained myself more, I am not moving data on the same failing hhd, I am moving it from 1 computer (the one with the failing hhd) 2 another computer, I have filled my home partition, so I want to use the root partition for a temp. storage until I get another hhd

I have a question with using "gksudo nautilus"  when I get done, how can I disable that command so that I am not using nautilus as root anymore?

---

### Post by mrhhug on 2011-01-29
you really should create a subdirectoy like sisco311 recommends i keep a /var/backup/ directory for various backups. if i was doing what your doing now i would put these files in that location.

close the nautilus window and then the terminal associated with it and you will have ended that privileged nautilus session.

---

### Post by hunterkasy on 2011-01-31
I used this command "gksudo nautilus" and I copied my files over to a folder I created under the root file system, now I have replaced my dying hhd and I have copied the files that I moved to the root system back over to the new hhd, the files have root permission, and I want the files permission back over to my user-name, how can I replace all the permissions for the files back over, I have all the files in one folder, can I change the permissions on everything in the folder instead of one at a time?

---

### Post by vanadium on 2011-01-31
You should probably not change the permissions. You should change the user and group back from root to your own login. This may also be performed graphically using a nautilus window with root permissions. On the commandline, "chown" changes permissions.

---

### Post by drewsus on 2011-01-31
the command you would want to use is: 
```
chown -R 1000:1000 /name/of/folder/you/want/to/do/this/to/recursively
```

For example, if you wanted to make yourself the owner of /home/user/test_folder and all the files and folders inside of it, run: 
```
chown -R 1000:1000 /home/user/test_folder
```

---

