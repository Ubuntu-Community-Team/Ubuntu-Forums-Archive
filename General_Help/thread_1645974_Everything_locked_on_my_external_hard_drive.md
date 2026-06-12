---
title: "Everything locked on my external hard drive"
date: 2010-12-15
forum: General Help
---

### Post by rapattack1 on 2010-12-15
Hi I have an external hard drive with many files on it and i can't do anything with them as none of them is accessable. They have the lock symbol and the cross. I thought i would be able to right click and change the permissions that way but it seems not. They were readable a few days ago when i had UBuntu 9 installed on this computer but i just installed Ubuntu 10....am i missing something? Thanks :0)

---

### Post by NCLI on 2010-12-15
> **rapattack1 said:**
> Hi I have an external hard drive with many files on it and i can't do anything with them as none of them is accessable. They have the lock symbol and the cross. I thought i would be able to right click and change the permissions that way but it seems not. They were readable a few days ago when i had UBuntu 9 installed on this computer but i just installed Ubuntu 10....am i missing something? Thanks :0)
The permissions were probably messed up during the upgrade.

Open a terminal, type "cd" then a space, then drag and drop your external disk from "Computer" into the terminal, and hit enter.

Now enter this command replacing USERNAME with your username:
```
sudo chown -R USERNAME:USERNAME ./
```
It will ask you for your password. Enter it, and ignore the fact that nothing seems to happen, then press enter.

It may take a few minutes, but you should be able to access your files again when the command is done.

---

### Post by rapattack1 on 2010-12-15
I dunno. I didn't have the external drive attached when i did the upgrade.
Gee now it is not mounting at all so i can't do anything. This has been a reliable drive.

---

### Post by rapattack1 on 2010-12-24
It is mounting again i think because of other changes ....can anyone help with the locking thing please????;)

---

### Post by QLee on 2010-12-24
[QUOTE=rapattack1]It is mounting again i think because of other changes ....can anyone help with the locking thing please????;)[/QUOTE]

You might get the best help if you provide more information. It can't hurt to mention what those "other changes" were.

You'd likely want to mention what filesystem the drive is formatted to.

You might get some benefit from these links:

Ownership and permissions of vfat / ntfs are set at the time of mounting.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Come back and post questions about anything you don't understand, there will be lots of people to help and you will, ultimately,  be successful.


[OT - Edit] Are you a smoke jumper, around here the fire crews that repel from choppers to fight fires in places that are hard to get to are called rapattack crews? No need to answer this off topic question, just wondered.

---

### Post by rapattack1 on 2010-12-24
Sorry i have a medical condition and am super unwell so i can't remember. Anyway i am just theorising. I don't know enough to know!

As I said it was working/readable/mounting fine before when i had ubuntu 9 installed and then when i plugged it back in the files had the lock on them. It was too long ago for me to know/remember about what it was formatted to.
OK will try and read those pages later. Xmas day in Australia now and have to rush to the rellies place. Thanks.

I don't know what your other statement means sorry! The rapattack id or username is because my street name is Rap Attack. :0)

---

### Post by rapattack1 on 2011-04-30
I had to end up formatting the hard drive and losing all the files. Working well again :0)

---

