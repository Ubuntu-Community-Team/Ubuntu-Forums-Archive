---
title: "USB External Hard Disk - ext4 - Help with Permissions setting"
date: 2009-09-08
forum: General Help
---

### Post by nomnex on 2009-09-08
Hi,

Fairly new to Ubunt/Linux.
I have formatted my external USB HD with gPart in ext4.

Since gPart needs root permission, the disk belongs to root.
I have aleady changed the permissions (read/write) others

If the disk was formatted in FAT32, there would be no permission.
So that's my question: where and how can I change that? How can I have the disk with ext4 mount as a fat32 volume (i.e. don't need permission and available to all user without restriction)

I don't want to format in Fat32 because the volume is large 500 GB and I use only with Ubuntu computers.

Thanks.

Either with the GUI either with the CLI, but please explain in plain English please. I am not an experienced user.

---

### Post by nothingspecial on 2009-09-08
You need to change the ownership of the disk to you.
```

sudo chown -R username:username /media/disk
```

And set read write and excecute permissions for anybody
```

sudo chmod -R 777 /media/disk
```

This will allow full access to any directories and subdirectories on the disk for anyone.

sustitute /media/disk for the correct path.

---

### Post by nomnex on 2009-09-08
@nothingspecial

Thank you. I know the chmod command with "RWX" but what does that mean?

```
-R 777
```After I format a USB HD, does it figure in the /etc/fstab?

Lastly to change ownership of the disk root > my name, is this correct?

```
sudo chown -R root:myname/media/disk
```Thanks again

---

### Post by nothingspecial on 2009-09-08
Numbers are just a different way of expressing ownership. The order is user, group and others.

7 = rwx
6 = rw-
5 = r-x
4 = r--

So permissions of 777 gives the owner, group and others rwx permissions.

The colon in the chown command seperates user and group. So if you wanted root and only root to own the drive it would be

```
sudo chown -R root:root /media/disk
```

Don`t forget the spaces.

The -R flag means and every directory and subdirectory within the directory you are changing the ownership of.

---

### Post by nomnex on 2009-09-08
Thank you, you explain clearly.

in fact the HD owner is root (default setting by gPart) and I want to change the ownership to me, aka "username" as advised, so what's the correct string?

```
sudo chown -R "?":"?" /media/disk
```> The colon in the chown command seperates user and groupso I wonder if the user and group are similar? It seems each time I create a new user, a group of the same name is also created. Is the following correct?

```
sudo chown -R "user: username":"group: username" /media/disk
```

---

### Post by nothingspecial on 2009-09-08
> **nomnex said:**
> Thank you, you explain clearly.

in fact the HD owner is root (default setting by gPart) and I want to change the ownership to me, aka "username" as advised, so what's the correct string?

```
sudo chown -R "?":"?" /media/disk
```so I wonder if the user and group are similar? It seems each time I create a new user, a group of the same name is also created. Is the following correct?

Each user has their own group.

> 

```
sudo chown -R [COLOR="Red"]"user: username":"group: username"[/COLOR] /media/disk
```

You just need to specify one user and one group. You can add users to groups. For example you may have a wife and children. You may have a directory that you only want your wife and yourself to have access to.

So you create a group, put you and your wife in it. If you own the directory but you set the group to you and your wifes new group,and give permissions of 660, then you (the owner - the first number) and the other members of the group (your wife - 2nd number) can read and write to it.

However others (ie the kids have no access to it).

---

### Post by nomnex on 2009-09-08
I see, thank you for your explanation nothingspecial. I can close the thread. See you.

---

### Post by nomnex on 2009-09-08
@nothingspecial:

BTW do you happen to know a good BASH tutorial for the commands (progressive and illustrated with easy to understand examples) from complete beginner to advanced? Thanks.

---

### Post by nothingspecial on 2009-09-09
Try [[COLOR="Magenta"]this[/COLOR]]("http://linuxcommand.gds.tuwien.ac.at/") one

---

