---
title: "Mounting folders"
date: 2011-01-03
forum: General Help
---

### Post by Captainnow on 2011-01-03
Hello.

I am running ubuntu server 10.10.
I have 3 hard drives. 
/dev/sda - 500 GB drive
/dev/sdb - 250 GB drive (os installed here) /
/dev/sdv - 500 GB dive

I have them formated as ext4 file system.
I do the following commands

sudo mount /dev/sda /home/username
sudo mount /dev/sda /home/share

These commands mount successfully.
The problem I am having is when I FTP or use samba to move files to just my /home/username directory it shows up also in /home/share directory. If I delete from one it deletes from the other. Why are they acting as if they are the same directory when they should be two separate unique directories?

---

### Post by QLee on 2011-01-03
> **Captainnow said:**
> Hello.

I am running ubuntu server 10.10.
I have 3 hard drives. 
/dev/sda - 500 GB drive
/dev/sdb - 250 GB drive (os installed here) /
/dev/sdv - 500 GB dive

I have them formated as ext4 file system.
I do the following commands

sudo mount /dev/sda /home/username
sudo mount /dev/sda /home/share

These commands mount successfully.
The problem I am having is when I FTP or use samba to move files to just my /home/username directory it shows up also in /home/share directory. If I delete from one it deletes from the other. Why are they acting as if they are the same directory when they should be two separate unique directories?

Are you sure you're mounting the devices, haven't you partitioned them into at least 1 partition, for example sda1? What is the command for mount that you are using, those that you wrote won't work, you would receive an error message?

---

### Post by tredegar on 2011-01-03
Leaving aside the fact that you have not partitioned your drives (not the way to go, but it'll probably work, most of the time)

> The problem I am having is when I FTP or use samba to move files to just my /home/username directory it shows up also in /home/share directory.

You have the same device, **/dev/sda** mounted in two different places 
 **/home/username** and **/home/share**

So the filesystems are identical, but mounted twice, in different places. Changes made to one will, of course, be reflected in the other (because they are _the same_ device).

What are you trying to achieve?

---

### Post by QLee on 2011-01-03
[QUOTE=tredegar]Leaving aside the fact that you have not partitioned your drives (not the way to go, but it'll probably work, most of the time)...[/QUOTE]

Not really something to leave aside in my opinion, this person is inexperienced in GNU/Linux although is posting in the General forum.

---

### Post by Captainnow on 2011-01-03
Yes I am new to linux and I apologize if I am posting in the wrong forum.

I have fixed the partition on the drive so it does have a /dev/sda1 now.

I now have used the command :
mount -t ext4 /dev/sda1 /home/username
mount -t ext4 /dev/sda1 /home/share

Same result they act as if they are the same directory.

What I want to do is mount just a single users home directory and the directory share to a different hard for more space for those 2 directories, but I want to keep them independent of each so I can have different files in each one.
I'm obviously doing something wrong.

---

### Post by Verbeck on 2011-01-03
> **Captainnow said:**
> 
I now have used the command :
mount -t ext4 [SIZE=2]**/dev/sda1**[/SIZE] /home/username
mount -t ext4 [SIZE=2]**/dev/sda1**[/SIZE] /home/share

Same result they act as if they are the same directory.

because you're just mounting the **same drive**
imagine /home/username and /home/share as shortcuts to the partition /dev/sda1

---

### Post by Captainnow on 2011-01-03
> **Verbeck said:**
> because you're just mounting the **same drive**
imagine /home/username and /home/share as shortcuts to the partition /dev/sda1

So You have to make a separate partition for every folder you wish to mount on a drive?

---

### Post by matt_symes on 2011-01-03
Hi

> **Captainnow said:**
> 
I have fixed the partition on the drive so it does have a /dev/sda1 now.

I now have used the command :
mount -t ext4 /dev/sda1 /home/username
mount -t ext4 /dev/sda1 /home/share

Same result they act as if they are the same directory.


They will do as they point to the same physical partition.

> What I want to do is mount just a single users home directory and the directory share to a different hard for more space for those 2 directories, but I want to keep them independent of each so I can have different files in each one.
I'm obviously doing something wrong.

Consider partitioning the hard drive into 2 partitions (eg. sda1 and sda2) and then mount them separately. Or mount it once and use symbolic links to 2 directories you have created on that partition.

Kind regards

---

### Post by Verbeck on 2011-01-03
> **Captainnow said:**
> So You have to make a separate partition for every folder you wish to mount on a drive?
yep. or as matt_symes suggested, mount /dev/sda1 to somewhere (ex, /mnt) and make symbolic links to the directories in the partition
ex;
sudo mount -t ext4 /dev/sda1 /mnt
sudo ln -s /home/share /mnt/actualsharedirectory

---

### Post by QLee on 2011-01-03
Captainnow, I know from reading your previous posts that you are familiar with Windows. Windows "mount" drives for you and assign drive letters but things are done a bit differently in Ubuntu. The volumes are mounted not as separate drives but in a location in the Linux filesystem that you choose. Those directories (folders) you specified are not folders on the "drive" they are only in the filesystem. That is what is meant by you've mounted the same drive in two places and thus it is the same file you're seeing in both places.


I found this link that might help, or you could come back with questions if any part of it is unclear. There are differences to learn when switching from Windows.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)


[Edit] I see while I was away looking you got that figured out. No problem with your question in the General forum, it's just that new users don't always find it and so sometimes people assume that the user is experienced, that's all I meant by my comment. We all want to help you get off to a good start.

---

### Post by QLee on 2011-01-03
> **Captainnow said:**
> ...
What I want to do is mount just a single users home directory and the directory share to a different hard for more space for those 2 directories, but I want to keep them independent of each so I can have different files in each one.
I'm obviously doing something wrong.

Well, the user's home is a bit of a special case, if you want a separate /home/username after the system has been installed and the home for that username has already been made in the filesystem, you'll need to investigate the topic moving a user's home.

Links for that:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If the share directory you want to make is to share with other users there are probably better places to locate it than in one specific user's home. Then you would create links as mentioned by matt_symes and Verbeck

---

### Post by Captainnow on 2011-01-05
Thanks for all the info. Now that I understand it better. I have partitioned my drive into two partitions and now it works the way I wanted it.

Sometimes just a better understanding is all that is needed. Thank you all.

---

