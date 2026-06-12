---
title: "Creating additional partition"
date: 2011-09-02
forum: General Help
---

### Post by quarternote on 2011-09-02
Hello,

I'm trying to make additional partition to be used for virtual machines.
I have managed to create it with gparted. Other portion of the drive is using ntfs and new partition i created is using ext4.
That drive does not contain any operating systems.

As i said i have partition created, but my user has no access to use it. I can't example create new folder. :confused:
Seems that only root have access to that partition.. Is it normal to need manually change credentials after creating new partition?

---

### Post by gdonwallace on 2011-09-02
If the drive does not have an OS installed, then yes that is normal.  Although it is formatted to a Linux format, and Linux can see that format and partition, until an OS is installed; only root will be able to see that partition.

---

### Post by quarternote on 2011-09-02
I have my operating systems installed in separate drives.
I just need this new partition for virtual machines.

When checking permissions from /media my ntfs storage drive have (drwxrwxrwx 1 root root) permissions
as my new ext4 partition has (drwxr-xr-x 3 root root).
I can create new folder in my storage drive just fine.

Should i just manually try to change credentials using chmod?
What kind of permission are appropriate to use this kind of situation?
Something like: chmod 660 /dev/sdxx ?

---

### Post by gdonwallace on 2011-09-02
With those permissions, root is the only user that would have access to that drive.  Also, the permissions restrict the drive to read and execute only.  

If all you are doing is setting the drive up for storage, then 666 permissions would work (I think that is the one that give read / write across the board, at work don't have my linux laptop with me)

I would also change owner from root:root to your login or to a group that your user plus anyone else is a member of so that anyone would be able to read / write to that drive.  usage chown to change owner ship.

Check out this URL for additional information on Linux commands:
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by quarternote on 2011-09-04
Ok. When i have some spare time i read through documentation about chmod and chown. I'm not very familiar with those permission and owner changes, so i should read before just changing those security related settings.
I will post back when done.

---

### Post by quarternote on 2011-09-04
I got it working.
I changed ownership for folder where drive is mounted.
Let's say drive name is DRIVE. So i needed to change ownership for folder /media/DRIVE.
For changing i used command:
```
sudo chown -v username /media/DRIVE
```
Thanks for your help gdonwallace.

---

