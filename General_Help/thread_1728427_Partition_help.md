---
title: "Partition help"
date: 2011-04-13
forum: General Help
---

### Post by oldskool on 2011-04-13
Hello 

I will admit i dont know how partitions work in ubuntu. 

I installed 10.10 on a fresh disk with just 40gb for the OS. 

I was planning on using the rest as a data drive. 

I have this 

```

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40960000   83  Linux
/dev/sda2            5100       30402   203237376    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris
/dev/sda6            5100       29165   193298432   83  Linux


```
However, i can't access sda6 which i would like to use for data. 

If i go places > computer... i do see a drive "250GB harddisk: 189gb filesystem"... I assume this is the free space mounted. However, inside that folder is "lost & found" with a x on it and i dont have permissions to write to the folder/space.

I'm just looking for some advice on how i can use/access this free space. 

I have gparted live cd and i've tried several things but 2bh i don't know what i am doing. :)

---

### Post by coffeecat on 2011-04-13
Boot into your 10.10 installation, not into a live session, and find and mount the 189GB filesystem partition (which I assume is your sda6) from the Places menu. When the nautilus file browser opens, press ctrl-L and the breadcrumb trail will change to a text path showing /media/something. "something" will be the mountpoint. Now open a terminal and:

```
sudo chown yourusername: /media/something
sudo chmod 777 /media/something
```Obviously, change the something to whatever it should be and change "yourusername" to your account name. Don't omit the trailing colon in the first command. This ensures that the filesystem is set to your default group.

The first command makes the filesystem owned by yourself and you will have no problems writing to it even if you remount it on a different mountpoint. The second command (which you can omit) gives the filesystem permissions for anyone else to write to the partition. Only really of use if you set up further accounts.

The lost+found folder is part of the filesystem. You can only access it as root. If you delete it, it will come back. Simply ignore it.

**EDIT**: Usually at this point someone comes in and says you have to run chown -R and/or chmod -R for a recursive chown or chmod. You don't. You only need the recursive option if you have already written files to the partition. The commands I have posted take advantage of a little-understood feature of Linux filesystems, that you can chown and chmod the root of the filesystem itself by means of the mountpoint.

---

### Post by oldskool on 2011-04-13
Dammm

Cant believe it was that simple

Thanks v.much 


I was reading about mount points and editing files for mounting drives etc etc.... 

:)

---

