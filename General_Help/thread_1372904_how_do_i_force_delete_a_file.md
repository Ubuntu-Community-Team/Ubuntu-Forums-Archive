---
title: "how do i force delete a file?"
date: 2010-01-05
forum: General Help
---

### Post by allmightymoo on 2010-01-05
Ok i'm runnign ubuntu using the live CD i already have ubuntu installed on my computer but it wont boot. I'm trying to delete the file causing the problem. SO is there a way to delete a file that is in the ubuntu installed on my computer from the ubuntu on the livecd?

if that doesnt make sense how can i delete a file in my ubuntu w/o actually being in ubuntu? haha...i need help...

---

### Post by Vaphell on 2010-01-05
1. mount the partition containing the file in question
2. delete the file
3. ???
4. profit


[http://ubuntuforums.org/showthread.php?t=343326](http://ubuntuforums.org/showthread.php?t=343326)

to get partition list
```
fdisk -l
```

---

### Post by allmightymoo on 2010-01-05
i forgot to mention that when i try to delete the file it says i dont have permission...i cant boot into ubuntu b/c of this file so  i'm trying to delete it in the ubuntu on the livecd...

---

### Post by bilol on 2010-01-05
Hi,
Follow the steps:
(1) Run ubuntu as live cd
(2)Manually mount the already installed ubuntu partition
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sdb1 /mnt/ubuntu
```
(3) navigate to the concerned files
```
cd /<path of the file>
```
(4) Delete the concerned file
```
sudo rm -rf <file name>
```
(5) If step (4) did not work,take all important backups and reinstall ubuntu. 

Hope this will help....

---

### Post by allmightymoo on 2010-01-05
This is what i get in the terminal with the first code...

[B]ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists[/B]

am i doing something wrong?

---

### Post by Leppie on 2010-01-05
> **allmightymoo said:**
> [B]ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists[/B]
you are trying to create something already existent.
if you want to check whatever is already in the /mnt folder, you can use the "ls" command:
```
$ls /mnt
```

---

### Post by bilol on 2010-01-06
Well,I give the name "ubuntu" as an example, unfortunately that folder already exists in your system.Therefore, in the first section of the code please replace two occurrences of the word "ubuntu" by "karmic".
Again /dev/sdb1 is an example of your linux partition. to know the exact name do the following:
(1) start installing from live cd
(2) choose **manual** partition manager 
(3) identify the ubuntu partion
(4) identify the file system of ubuntu (ext2 or ext3)
(5) cancel installation

So the first section of the code might look like:
sudo mkdir /mnt/karmic
sudo mount -t ext2 /dev/sdb1 /mnt/ubuntu

Now follow the steps as mentioned in my previous thread

---

### Post by bilol on 2010-01-06
**correction:**
So the first section of the code might look like:
```
sudo mkdir /mnt/karmic
sudo mount -t ext2 /dev/sda1 /mnt/karmic
```
or
```
sudo mkdir /mnt/karmic
sudo mount -t ext3 /dev/sda5 /mnt/karmic
```

---

