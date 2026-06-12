---
title: "moving /home to another partition"
date: 2010-05-27
forum: General Help
---

### Post by akg_nitt on 2010-05-27
hi! this is my first thread on this forum
as an Ubuntu novice,i have few curious questions in mind which seeks an explanation here
currently i m using 500Gb hard disk with root partition 20GB and rest as FAT partition.
currently /home resides in the root partition itself.but as would be saving all my work in this directory itself,it warns to get consumed soon which can deteriorate my system's performance.
i can mount my /home directory to the FAT partition but the problem lies in the fact that as i possess a removable disk(hard disk i mentioned),i can end up corrupting that partition while using it with other windows system .
in this case i wont be able to login into my account as nautilus ,sanity check and few other things wont work according to my understanding of Linux.
i can very well retain the /home directory where it is and can mount the other partition to something like /mnt/windows and start using it.but i wont get a sense of satisfaction in that as i intend to work according to the existing structure in ubuntu ie would like to download only in /home/downloads etc.
i thought of creating soft links to folders like Desktop ,Downloads and Videos to the FAT partition so that i can keep working according to the way its designed and simultaneously avoid my root partition getting spaced out.
but again in the case of corruption in FAT partition,will there be problem in login as nautilus would try to run nautilus /home/username /desktop etc.(but all the soft links will be junk)  so it will throw error but  whether in this case despite these errors would i be able to login succesfully in UI.
waiting for response and suggestions which can help out the issue

---

### Post by dabeej on 2010-05-27
You can't and shouldn't use FAT for a home directory. Just save stuff there on that FAT partition that you may need to have on both windows and linux.

---

### Post by akg_nitt on 2010-05-27
thanks 4 ur comment
i have mounted FAT partition to /media/my_data but i have no permissions to write into it.
how can i obtain such permission in my account(which is there is sudoers list).

---

### Post by Roasted on 2010-05-27
By one of two ways:

ALT + F2 "gksudo nautilus" hit enter and type in your root password. Navigate to /media and find the my_data folder. Right click - properties - permissions. Set the permissions accordingly to what work for you. Do you want more than 1 user to have access? You could set all 3 levels to "create and delete files" which is full control, basically. Or you can add all users to a group, log out/back in to activate the group, and set the group + "create and delete files" to my_data. Then the users should be able to access it accordingly. DO NOT do anything else with gksudo nautilus. Just do what's necessary (in your case, changing permissions) and exit that window.

OR

Applications - Accessories - Terminal

sudo chmod 777 /media/my_data

chmod = change permissions.
777 = full control for owner/group/all users. This folder would be WIDE OPEN! If you want owner/group to have full access, but only read access for other users, use 775. If you want owner/group to have full access, but NO access to other users, use 770. This can be customized any way that you need. 

Each digit resembles the level of permission + who it belongs to.

7
7
7

1st 7 = Owner
2nd 7 = Group
3rd 7 = Others

7 = Create and Delete files (full control)
5 = Read/execute access (limited control)
0 = No access.

---

### Post by akg_nitt on 2010-05-27
also not seeing my drive as a seperate disk or Computer.
i changed my fstab to
UUID=6D7A-B1D4                           /media/my_data     vfat   auto,users,rw 0 0
still the partition is read only

---

### Post by akg_nitt on 2010-05-27
tried
sudo chmod 777 /media/my_data
with no luck
its still readonly
the partition has multiple mount points,does that has to do anything with the problem
1)/media/my_data
2)/mnt/my_data

when trying to unmount sudo umount /mnt/my_data recieving error device busy.
comments??

---

### Post by jerome1232 on 2010-05-27
chmod won't work on a fat file-system, Microsoft file systems and linux file-systems don't understand each other.

The permissions are setup at mount time.

Completely unmount that thing, then mount it with these options (I think that should work at least)

```
sudo mount -t vfat UUID=6D7A-B1D4 /media/my_data -o defaults,umask=000
```

---

### Post by akg_nitt on 2010-05-28
cheers!!!
things just worked fine
steps i followed
first removed the line from /etc/fstab which was mounting partition
then sudo umount /dev/sda5
then mounted in the way told above.
was able to mount it with write permissions.

PS:in ubuntu by default a partition is mounted to /media/"label"
in this way the mount partition created has user r w x permissions without any trouble
but if u try to create a dir in /media 
say sudo mkdir /media/my_data
it will have ownership of root
so when u mount the partion in this directory it is mounted as read only and so was the problem in my case, doing
sudo mount -t vfat UUID=6D7A-B1D4 /media/my_data -o defaults,umask=000
will make all the directories "world write" and it is confirmed with the green colour in background.
we can change ownership to local user by sudo chown user /media/my_data and then mount the partition, i think in this case also we ll able to read write execute on it(not tried,correct me if i m wrong).

thanks@all: things posted here helped me clear my head on ubuntu

---

### Post by jerome1232 on 2010-05-28
This is a pretty good post that explains mounting and fstab a bit, if you search through and find the section about fat / ntfs it should help you to understand it a bit better. Your on the right track but because it's a fat file-system it breaks the rules a bit, also the ownership of the mount point prior to mounting doesn't matter a bit. It can all be configured with the different mount options.

I forgot the link to the fstab post lol

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

