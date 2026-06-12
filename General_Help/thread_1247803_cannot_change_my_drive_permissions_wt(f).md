---
title: "cannot change my drive permissions? wt(f)"
date: 2009-08-23
forum: General Help
---

### Post by neoroses on 2009-08-23
safe guys, this is a bit of a odd one i think.

i have my 500 gig hard drive on my main pc, which works perfectly allthe time, however i have just attempted to share it over the network and i get this message:

net usershare' returned error 255: net usershare add: cannot share path /media/disk as we are restricted to only sharing directories we own

now i have attempted to change the drive ownership to me (sam) using

```
 sudo chown -R sam:sam /media/disk

```

and chmod 777 still with no avail, any ideas how i can change the permissions to sam so i can share it?

safe thanks

---

### Post by tomasrey88 on 2009-08-23
It looks like Sam here is having the same/similar problem to my problem: 
[http://ubuntuforums.org/showthread.php?p=7833754#post7833754](http://ubuntuforums.org/showthread.php?p=7833754#post7833754) . Can one of you superusers please show us the way? (pretty please). 

Thanks guys!
:P

P.S. Since I've found half a dozen of us with the same problem already, After we've found the solution, I'll offer to the mods to post a detailed how-to as a sticky at the top of this page or on the "community documentation".

---

### Post by neoroses on 2009-08-23
i second the notion for a Congregational howto :) please help us fix this i need my media in my bed!!!!

but please note im attempting to do this with a internal SATA not usb

---

### Post by drs305 on 2009-08-23
> **neoroses said:**
> safe guys, this is a bit of a odd one i think.

i have my 500 gig hard drive on my main pc, which works perfectly allthe time, however i have just attempted to share it over the network and i get this message:

net usershare' returned error 255: net usershare add: cannot share path /media/disk as we are restricted to only sharing directories we own

now i have attempted to change the drive ownership to me (sam) using

```
 sudo chown -R sam:sam /media/disk

```

and chmod 777 still with no avail, any ideas how i can change the permissions to sam so i can share it?



Is this a fat32 or ntfs filesystem. If so, permissions are set at the time of mounting and can't be changed. 

To change the ownership or permissions, they must be accomplished from within the mount command itself: either via command line or with switches on the applicable line in fstab. 

By default, non-linux filesystems are generally mounted and owned by root, with the user having read/write privileges even though the partition is owned by root.

---

### Post by neoroses on 2009-08-24
how do i go about making it possible to share over the network then?

---

### Post by drs305 on 2009-08-24
> **neoroses said:**
> how do i go about making it possible to share over the network then?

In nautilus, right click on the folder you want to share, select Properties, then the Share tab and set the share properties.

---

### Post by neoroses on 2009-08-24
no lol. thanks for the advice but it doesnt appear to be that simple.

it is owned by root and not me, so i cannot share it it simply wont let me, however i cannot change the ownership of the drive no matter what i do.

---

### Post by drs305 on 2009-08-24
> **neoroses said:**
> no lol. thanks for the advice but it doesnt appear to be that simple.

it is owned by root and not me, so i cannot share it it simply wont let me, however i cannot change the ownership of the drive no matter what i do.

If this is a non-linux filesystem (fat, ntfs), did you accomplish the steps discussed previously about mount options? If you don't alter the mount options for these file systems the mount point will always be owned by root. You must ensure you are the owner at the time of mounting - either with the mount command or through fstab. This normally means including "uid=1000" in the fstab options section (if you are user 1000).

If it is an ext3 file system, make sure you are the owner of the mount point before you mount the partition.

If you are going to put the mount instructions in fstab, here are a few links:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by neoroses on 2009-08-24
i have set it to auto mount in fstab and it looks like this:

```
/dev/sda1 /media/disk ntfs-3g defaults,user,locale=en_US.UTF-8 0 0
```

is this rite? thanks :)

---

### Post by drs305 on 2009-08-24
> **neoroses said:**
> i have set it to auto mount in fstab and it looks like this:

```
/dev/sda1 /media/disk ntfs-3g defaults,user,locale=en_US.UTF-8 0 0
```

is this rite? thanks :)

You have to add the uid option (assuming you are user 1000):
```
/dev/sda1 /media/disk ntfs-3g defaults,user,uid=1000,locale=en_US.UTF-8 0 0
```

---

### Post by Katalog on 2009-08-24
You might try using PySDM. It allows you to change a wide variety of drive settings in a graphical environment. Helped me out with some external drive and partition troubles a couple of times.

---

### Post by neoroses on 2009-08-24
i love you :)

---

### Post by neoroses on 2009-08-24
tho i am nowthe owner i still cannot share, i get this message

```
'net usershare' returned error 255: net usershare add: failed to add share videos. Error was Operation not permitted
```

any ideas?

hang about, i dun it now

---

### Post by drs305 on 2009-08-24
Is *videos* one of the subfolders? If so, did you enable sharing on that folder as well?

---

