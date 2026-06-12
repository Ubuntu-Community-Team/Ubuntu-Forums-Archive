---
title: "mounting partitions with Guest user"
date: 2012-01-07
forum: General Help
---

### Post by jsandhu on 2012-01-07
Hi,

I have 4 partitions on my harddrive

1- systemfiles 
2- fat1 
3- fat2
4- fat3

now here is the thing, I made a new user (I am using ubuntu 11.04 and I am the default user) and called it Guest, I logged on it to check but I couldn't see any fat32 partition on it, all I want is the partition fat1 and fat2 to be available on the Guest account but not the fat3 one.

the user who will be using the Guest account is greater n00b than I am so all I want is as far as he is concerned the only partition he should be able to access is fat1 and fat 2. that's it, How should I do it?

Thanks

---

### Post by kimda on 2012-01-07
You could add these partitions to fstab so that they would be mounted on each startup.  


Here is a link to get you started. 
[GUI Fstab Editing with PySDM ]("ubuntuforums.org/showthread.php?t=872197")

---

### Post by jsandhu on 2012-01-07
see the problem is, if I leave the fat3 unmounted from Mount Manager the Guest clicks on it and it gets mounted.. so Mount Manager doesn't solves what I am trying to achieve, I want the Guest user to have no access what so ever to fat3.

---

### Post by killermist on 2012-01-07
Interesting question.

Possible solutions.
1.) create a group "lsdiscs" (low security discs) and make all the users members of lsdiscs and chown the devices to group lsdiscs.  Possible problem, not sure how to make certain devices persistently owned by a non-default group (maybe a udev rule change, not sure)

2.) create redundant fstab entries for the specific devices with a "mount option" (like with noatime, sync, and what-not) of "user=guest" to allow the guest to mount them.
Maybe /mnt/fat1 and /mnt/fat2 for normal mounts (only done by automount or your user) , and /home/guest/fat1 and /home/guest/fat2 mounted by guest, as guest.

---

### Post by jsandhu on 2012-01-07
> **killermist said:**
> Interesting question.

Possible solutions.
1.) create a group "lsdiscs" (low security discs) and make all the users members of lsdiscs and chown the devices to group lsdiscs.  Possible problem, not sure how to make certain devices persistently owned by a non-default group (maybe a udev rule change, not sure)

2.) create redundant fstab entries for the specific devices with a "mount option" (like with noatime, sync, and what-not) of "user=guest" to allow the guest to mount them.
Maybe /mnt/fat1 and /mnt/fat2 for normal mounts (only done by automount or your user) , and /home/guest/fat1 and /home/guest/fat2 mounted by guest, as guest.

hm.. not sure I understand even 10% of that, sorry I am such a noob.

one other thing I just learnt if I chose my fat32 partitions to be auto mounted on boot by PySDM, then I lose total control over them, I can't create a folder, can't delete any file also I can't download a file through my browser directly into the fat32 partition when before when I just use to open nautilus and click on the partition to mount it and I was able to do all those things, Thank god I made a back up of my fstab and I just removed the Mount Manager and restored my fstab file back.

although this way my fat32 partitions are not auto mounted and I have to click on each of them one by one to mount them but atleast then they work in a normal way.

---

### Post by killermist on 2012-01-07
Looking back, and thinking again about the original question:
Have you considered copying the content of fat3, reformatting the partition as ext3 or similar, and copying the content back so Linux can enforce good security standards (ownership/groupship/permissions)
Fat has NEVER been known for security of ANY type.

---

### Post by Morbius1 on 2012-01-07
These are examples of entries in fstab:
```
UUID=C4DB-C1B0 /media/fat1 vfat defaults,utf8,gid=plugdev,umask=007 0 2
```That will allow every local user ( by default every user you create through the GUI is a member of plugdev ) to access the partition.
```
UUID=C4DB-C1B4 /media/fat3 vfat defaults,utf8,uid=1000,umask=077 0 2
```This will make the owner of the partition you ( uid=1000 ) with access allowed only to you ( umask=077 - A "7" turns off all access and their position in the umask option applies to everyone other than the owner )

Just edit fstab by hand and run the following command to test for errors in what you've done in fstab and mount the partitions:
```
sudo mount -a
```To find the correct UUID number run the following command:
```
sudo blkid -c /dev/null
```

---

### Post by jsandhu on 2012-01-07
> **Morbius1 said:**
> These are examples of entries in fstab:
```
UUID=C4DB-C1B0 /media/fat1 vfat defaults,utf8,gid=plugdev,umask=007 0 2
```That will allow every local user ( by default every user you create through the GUI is a member of plugdev ) to access the partition.
```
UUID=C4DB-C1B4 /media/fat3 vfat defaults,utf8,uid=1000,umask=077 0 2
```This will make the owner of the partition you ( uid=1000 ) with access allowed only to you ( umask=077 - A "7" turns off all access and their position in the umask option applies to everyone other than the owner )

Just edit fstab by hand and run the following command to test for errors in what you've done in fstab and mount the partitions:
```
sudo mount -a
```To find the correct UUID number run the following command:
```
sudo blkid -c /dev/null
```


you sir, hit the Bulls EYE :D

here's what I did, I found the UUID with the code you provided :
```
sudo blkid -c /dev/null
```

then for my fat1 and fat2 partitions applied this code :
```
UUID=C4DB-C1B0 /media/fat1 vfat defaults,utf8,gid=plugdev,umask=007 0 2
```

and for my fat3 partition applied this one :
```
UUID=C4DB-C1B4 /media/fat3 vfat defaults,utf8,uid=1000,umask=077 0 2
```

and mounted them with sudo mount -a (they all mounted sweetly)

but to check I switched to the Guest account and Wallah! only fat1 and fat2 was visible there like fat3 did not even existed, but to recheck I restarted and logged into the Guest user first same thing again, fat3 invisible.

and not only that now all the partitions automount when i log on and I have full control over the files, I can edit them add them delete them :grin:


Thanks a lot sir!!!! :), YOU ARE GENIUS =D>=D>

---

