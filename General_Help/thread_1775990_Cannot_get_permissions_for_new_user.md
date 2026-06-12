---
title: "Cannot get permissions for new user"
date: 2011-06-05
forum: General Help
---

### Post by bob-linux-user on 2011-06-05
I am using Ubuntu 11.04 Natty (In case it is relevant it is with the gnome desktop ,I have an old graphic card)

I want add my wife as a second user. As I am pretty sure she is not a cyber terrorist I want to give her all the same privileges and access that I have.

I went to "Admin" then "users and groups" I added a new account with her name, gave the "administrator" account type and on the advanced settings, user privileges tab I ticked all the boxes.On the advanced tab I left all the defaults and put her in the "Main Group" for her name.

Now the problem is I have an ntfs partition with data on it. When she logs on she cannot see the partition. (Of course when I log on I can). When you browse to it via media it says you do not have the permissions necessary to view the contents.

How can I give her all the same privileges and access that I have please?

---

### Post by raja.genupula on 2011-06-05
> **bob-linux-user said:**
> I am using Ubuntu 11.04 Natty (In case it is relevant it is with the gnome desktop ,I have an old graphic card)

I want add my wife as a second user. As I am pretty sure she is not a cyber terrorist I want to give her all the same privileges and access that I have.

I went to "Admin" then "users and groups" I added a new account with her name, gave the "administrator" account type and on the advanced settings, user privileges tab I ticked all the boxes.On the advanced tab I left all the defaults and put her in the "Main Group" for her name.

Now the problem is I have an ntfs partition with data on it. When she logs on she cannot see the partition. (Of course when I log on I can). When you browse to it via media it says you do not have the permissions necessary to view the contents.

How can I give her all the same privileges and access that I have please?


--->change to root user 
and mount that file system from terminal 
-->are you both have a same group id  ?

dont mind if not work

---

### Post by bob-linux-user on 2011-06-05
Thanks Raja.

I am not sure how to browse from the terminal. When I did gksudo nautilus from the command line I was able to browse to the partition and open the files. I have set us both to the same group, which does not make any difference. When I switch back to my wifes account the partition is no longer visible.

---

### Post by tredegar on 2011-06-05
If you **ls -l /media** you'll see the permissions will not allow your wife access.

Might be easiest to make an entry for the drive in **fstab** that'll mount it at boot with the correct permissions.
The ubuntu documentation for **fstab** is [here]("https://help.ubuntu.com/community/Fstab")
You'll need to do create a mountpoint
```
sudo mkdir /mnt/windows
```
and then add an entry to **fstab** something like this (can't check as no win here, sorry) with **sudo nano /etc/fstab**
```
/dev/sda3 /media/windows  ntfs-3g defaults 0 0
```
(assumes your ntfs partition is /dev/sda3)
or
```
UUID=*12444F0392CEB83* /media/windows  ntfs-3g defaults 0 0
```
Get *your* ntfs partition's UUID with **sudo blkid**

Once fstab is fixed up **sudo mount -a** should mount your drive in the correct place (**/mnt/windows**) with 777 permissions, which means anyone logged in can do anything to it.

---

### Post by bob-linux-user on 2011-06-05
Thanks Tredegar. You pointed me in the right direction although I (sort of) "cheated" a bit I used pysdm to mount the partition,which if I understand it correctly edits the fstab file for you.

It all works ok now thanks.

---

