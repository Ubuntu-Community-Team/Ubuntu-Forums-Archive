---
title: "Problems after formatting my external hard drive"
date: 2010-02-01
forum: General Help
---

### Post by urbeg on 2010-02-01
I have a 250GB external hard drive that I want to format to ext4. It will be used to store back ups of my documents, music and pictures.

I tried booting the Ubuntu 9.10 Live CD (amd64) and using gparted to delete the partitions that where on the hard drive leaving only unallocated space, then creating one new partition that was ext4. I clicked apply and after a short time it said all operations completed successfully.

Now the problem is it won't let me transfer any documents onto the hard drive, or even create a folder or file.

If I go into the properties of the hard drive, under the permissions tab it says I am not the owner...?

Any help would be kindly appreciated.

---

### Post by audiomick on 2010-02-01
Hallo.
It has been mounted with root ownership.
I would try the GUI route first, although there is also a terminal command.

I am assuming you are no longer in the live CD, but have rebooted and found the drive in your normal install.

In the terminal
```
gksu nautilus
```
will open the file manager with root privileges. Be careful with this, it gives you the right to break you system if you do something wrong.

Now you should be able to right click on the new partition in this instance of the file manager and change it's permissions to what you need them to be.

---

### Post by Monotoko on 2010-02-01
You will need to put an entry for it in the /etc/fstab and then change the permissions to your own, in order to this you will need the terminal and the following commands, first unmount the harddrive, then run:

```
sudo fdisk -l
```

Find the partition on the storage drive that you would like to mount, and keep a note, for this example il use /dev/sdb1.

```
sudo mkdir /media/storage
gksudo gedit /etc/fstab
```

Then in that file put:

```
/dev/sdb1     /media/storage ext4          defaults,noatime        0      0
```

Remember to replace /dev/sdb1 with your own partition, next thing to do is give you write access, unplug and plug back in the device and ensure it has automatically mounted at /media/storage, then run:

```
sudo chmod -R 777 /media/storage
```

---

### Post by coldraven on 2010-02-01
I had the same problem so I decided to format it as NTFS instead.
Now I can use it to backup my XP box as well as Ubuntu.

---

### Post by urbeg on 2010-02-01
Thanks for the responses.

I was just wondering before I try out your suggestions was there any other way to format my external hard drive instead of using gparted on the Ubuntu 9.10 Live CD.

Maybe that's why I'm having this issue.

---

### Post by egalvan on 2010-02-01
> **urbeg said:**
> 
 was there any other way to format my external hard drive instead of using gparted on the Ubuntu 9.10 Live CD.


Do you have a working install of Ubuntu? 
If so, then you can use gparted while running your regular Ubuntu.
Since the drive will be used to *store back ups of my documents, music and pictures...*, no system files will be on it,
so just highlight it under gparted, un-mount it, and you perform any drive or partition operation on it.

As to other software other than gparted...
there are command-line tools that can be used.


running a LiveCD, all file ops will be run with "root" as owner.
(LiveCd does not have a user, as such)
But a "chown" command should clear this up.

---

### Post by Morbius1 on 2010-02-01
> **urbeg said:**
> Thanks for the responses.

I was just wondering before I try out your suggestions was there any other way to format my external hard drive instead of using gparted on the Ubuntu 9.10 Live CD.

Maybe that's why I'm having this issue.

When you formatted the partition as ext4 it became an extension of the root file system. As such it will mount with root as the owner and have permissions for read / write to root and read only for everyone else.

You can either take possession of it by using a:

sudo chown urbeg:uberg /media/whatever

Or leave the owner as root but change permissions to allow read / write to everyone:

sudo chmod 0777 /media/whatever

---

### Post by urbeg on 2010-02-04
Thanks for all your replies.

I got it working fine now.

I done what audiomick said and it work first go.

Many thanks

---

