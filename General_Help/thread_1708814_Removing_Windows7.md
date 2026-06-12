---
title: "Removing Windows7"
date: 2011-03-17
forum: General Help
---

### Post by leviathan8 on 2011-03-17
Hello. The time has came to realize that Windows does nothing useful for me expect the fact that it's using hard drive space without a reason. Yes, in other words, I just want to get rid of it. I would like to ask some questions in this thread regarding this action.

First of all, to my knowledge, I have to delete both windows partitions (in my case sda1 (as system reserved) and sda2 as the w7 partition itself) using GParted (or any other partitioning software). Then, the job is considered done, but, I do want to use the unallocated partition for a new partition, as it will be used as data storage. This looks fairly simple, but I'm a bit afraid of this. Maybe I'm just paranoid, but I feel unsafe when playing with partitions (moving boundaries especially) as GRUB can throw me an error message at any time. Does any of you know the consequences of such actions? I would be happy if someone could provide me a link with all the GRUB errors that can happen after partitioning and a way to fix them. 

So, here is the scenario: 


[LIST]
[*]delete windows 7 partition and it's system reserved
[*]create a new partition using the unallocated space (from both partitions, of course)
[*]boot into Ubuntu, *sudo grub-update* and windows 7 entry is gone.
[/LIST]
Now, I would like to disable GRUB to show upon boot, so it automatically drops me into Ubuntu. Is this possible? If not, there is still the option of setting the 1 second waiting time to choose.

I believe that this is all for now, thank you for according your time reading and I hope that anyone can enlighten me with the few things that I am unsure about. Have a nice day.

---

### Post by pqwoerituytrueiwoq on 2011-03-17
you could expand your linux partition instead of making a partition
legacy grub or grub 2?
open up gparted and delete the windows partition and do what you like with the space

gparted is not installed onto the machine be default but it is on the live cd (at least on ubuntu)

---

### Post by Vi3tHoneyX on 2011-03-17
You don't need to LiveCD Gparted. You can just install it in your current Ubuntu installation. ```
sudo apt-get install gparted
```1. Delete Windows 7 and setup your new partition using Gparted from your Ubuntu install

2. **THIS IS THE MOST IMPORTANT PART!**```
sudo update-grub
```3. GRUB should automatically disappear but if not then you can use "Startupmanager" to configure GRUB. :)


The problem with LiveCD is that your GRUB will probably flip out when you try to reboot into your installation of Ubuntu. Then it will cause you more time to reinstall GRUB

---

### Post by Hippytaff on 2011-03-17
You could delete the Windows partitions (using Gparted from the live CD or from the ubuntu install if you install it) and format the as EXT4 calling it /data and you should have a data partition do do with as you will. As long as grub isn't moved or tampered with a **sudo update-grub** should recognise the change but you need to edit fstab for the partition to mount as normal (back up your data, because things can go wrong whrn mesing around with partitions)
 
Also if there is no other OS on your hard drive then you won't see the grub menu (unless you press shift at boot)

---

### Post by pqwoerituytrueiwoq on 2011-03-17
> **Vi3tHoneyX said:**
> You don't need to LiveCD Gparted. 
if you want to resize your only ubuntu partition you do (resizing has its risks):lolflag:

---

### Post by Hippytaff on 2011-03-17
> **pqwoerituytrueiwoq said:**
> if you want to resize your only ubuntu partition you do (resizing has its risks):lolflag:
 Indeed /home needs to be unmounted if you don't want to encounter problem so liveCD is safer - but back up none the less

---

### Post by Vi3tHoneyX on 2011-03-17
> **leviathan8 said:**
> 
[LIST]
[*]create a new partition using the unallocated space (from both partitions, of course)
[/LIST]

He said to create a new partition ^_^

---

### Post by Hippytaff on 2011-03-17
> **Vi3tHoneyX said:**
> 
[/LIST]
He said to create a new partition ^_^
 
He did - but just incase ;-)

---

### Post by oldfred on 2011-03-17
The only issue if using the gparted you can download into your working Ubuntu is that any partition you want to edit cannot be mounted.

I regularly use gparted, but usually on another drive. I have so many partitions on my main Ubuntu drive that most (including my install) are in the extended partition. Then I cannot unmount the extended as if any logical is mounted then the extended is mounted by default.

So have second thoughts. You may want to back up windows. 
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

If you create a data partition then you have to edit fstab to mount it. You may have to set permissions and ownership to get it to work.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Using fstab gives you a permanent mount which would be preferred. But to test. This mounts it off / (root). You could use /mnt/data or ~/data which is /home/{yourID}/data.

$ sudo mkdir /data
$ sudo mount /dev/sda5 /data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /data
sudo chown -R fred:fred /data
where fred should be your login name

---

### Post by leviathan8 on 2011-03-17
Firstly, I thank you all for the quick replies.

> **pqwoerituytrueiwoq said:**
> you could expand your linux partition instead of making a partition
legacy grub or grub 2?
open up gparted and delete the windows partition and do what you like with the space

gparted is not installed onto the machine be default but it is on the live cd (at least on ubuntu)

I do not want to expand the linux partition, and I couldn't even do that as the windows partitions are not in the extended partition where Linux is located. To my understanding, I have GRUB2 (version 1.97 as it shows upon boot). 

> **Vi3tHoneyX said:**
> You don't need to LiveCD Gparted. You can just install it in your current Ubuntu installation. ```
sudo apt-get install gparted
```1. Delete Windows 7 and setup your new partition using Gparted from your Ubuntu install

2. **THIS IS THE MOST IMPORTANT PART!**```
sudo update-grub
```3. GRUB should automatically disappear but if not then you can use "Startupmanager" to configure GRUB. :)


The problem with LiveCD is that your GRUB will probably flip out when you try to reboot into your installation of Ubuntu. Then it will cause you more time to reinstall GRUB

Thanks for that tip. I never thought of the idea that GRUB would fail after reboot.

> **Hippytaff said:**
> You could delete the Windows partitions (using Gparted from the live CD or from the ubuntu install if you install it) and format the as EXT4 calling it /data and you should have a data partition do do with as you will. As long as grub isn't moved or tampered with a **sudo update-grub** should recognise the change and the partition should mount as normal (back up your data, because things can go wrong whrn mesing around with partitions)
 
Also if there is no other OS on your hard drive then you won't see the grub menu (unless you press shift at boot)

I'm at loss here. What do you mean that if *"grub isn't moved or tampered with a **sudo update-grub** should recognise the change and the partition should mount as normal"*?
If I execute the update-grub the new partition would not be seen or what?

---

### Post by pqwoerituytrueiwoq on 2011-03-17
> sudo chown -R fred:fred /data
where fred should be your login name
Cant you just use [I]sudo chown -R $USER:$USER /data
[/I]if you are confused [I]echo $USER
[/I]

---

### Post by pqwoerituytrueiwoq on 2011-03-17
since you want to replaced the win 7 partition 
why delete and create when you can format to ext4?

---

### Post by Hippytaff on 2011-03-17
I guess deleting and then formatting will allow the partitions to become one rather than two seperate ext4 partitions!?
 
That was my thinking anyway, but I quite often miss the point :?

---

### Post by leviathan8 on 2011-03-17
> **oldfred said:**
> The only issue if using the gparted you can download into your working Ubuntu is that any partition you want to edit cannot be mounted.

I regularly use gparted, but usually on another drive. I have so many partitions on my main Ubuntu drive that most (including my install) are in the extended partition. Then I cannot unmount the extended as if any logical is mounted then the extended is mounted by default.

So have second thoughts. You may want to back up windows. 
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

If you create a data partition then you have to edit fstab to mount it. You may have to set permissions and ownership to get it to work.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Using fstab gives you a permanent mount which would be preferred. But to test. This mounts it off / (root). You could use /mnt/data or ~/data which is /home/{yourID}/data.

$ sudo mkdir /data
$ sudo mount /dev/sda5 /data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /data
sudo chown -R fred:fred /data
where fred should be your login name

Is this fstab editing really necessary? I just want to create a new partition, why Ubuntu wouldn't be able to mount it?

> **Hippytaff said:**
> I guess deleting and then formatting will allow the partitions to become one rather than two seperate ext4 partitions!?
 
That was my thinking anyway, but I quite often miss the point :?

Yes, you get the point. I delete both partitions and make one. :)

---

### Post by Vi3tHoneyX on 2011-03-17
Ubuntu by default will mount on demand extra partions/drives. Editing the fstab will auto mount the new partition with Ubuntu startup. ^_^

---

### Post by leviathan8 on 2011-03-17
> **Vi3tHoneyX said:**
> Ubuntu by default will mount on demand extra partions/drives. Editing the fstab will auto mount the new partition with Ubuntu startup. ^_^

Well, I'm fine with that. I never really used fstab and I don't consider it as a necessity. 

Thank you for your answers, everyone.

---

### Post by Hippytaff on 2011-03-17
Your welcome - if your happy the issue is resplved remember to mrk the htread as solved in the thread tools at the top of the page :-)

---

### Post by leviathan8 on 2011-03-17
Damn.... I just created the new partition and it says that it's unable to detect filesystem (ext3). Possible reasons are: 
* the fs is damaged
* the fs is unknown to GParted
* there is no fs available (unformatted)

What do?

EDIT: Nevermind... just restarted and it works like a charm. I believe that this is a GParted bug? Permissions added. Now my laptop is purely Linux. :D
Thanks again for help.

---

### Post by pqwoerituytrueiwoq on 2011-03-17
was thinking there was only one partition 
i installed 7 to a very small part of my hdd (too small to have a recovery partition)
it is only there so best buy can say yes your battery needs replacing
then i will delete it

---

### Post by pqwoerituytrueiwoq on 2011-03-17
unable to detect the blank one you just made?
if so i would just reformat that one
if you need to recover 
change sda5 to what ever partition needs recovering
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

---

