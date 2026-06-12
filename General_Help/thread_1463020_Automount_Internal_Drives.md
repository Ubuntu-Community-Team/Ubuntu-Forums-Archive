---
title: "Automount Internal Drives"
date: 2010-04-26
forum: General Help
---

### Post by arjunbajaj on 2010-04-26
How to automount internal drives. I have 2 other partitions other than the boot one. I want both the other partitions to mount at startup.......without asking me the password.......

thanx........:)

---

### Post by cdenley on 2010-04-26
People may be more inclined to help you if you didn't use that annoying large font.

---

### Post by bcbc on 2010-04-26
Add whatever you want to mount to /etc/fstab 
```
sudo blkid
```
This lists your partitions and provides their UUID and file system type.
Then make a directory for the one's you want to mount
```
sudo mkdir /media/SomeName
```
Then open up fstab for edit
```
gksudo gedit /etc/fstab
```

Add a line for each partition you want to mount replacing xxx with the UUID of the partition shown by the blkid command above - if it's not an ntfs partition, change the part in bold below as well:
```
UUID=xxx /media/SomeName **ntfs** defaults 0 0
```

You can reboot to take effect, but better is to mount immediately using 
```
sudo mount -a
```

Edit: if it's ntfs no point is setting pass to 2 (since fsck won't do anything). If it's ext2/3/4 you can set it back to 2 (the last zero on the line in fstab)

---

### Post by cariboo on 2010-04-26
This isn't a security question, Moved to General Help.

---

### Post by arjunbajaj on 2010-04-27
Sorry cdenley for putting a large font. I'll not do that from now on.
Thanks bcbc for your help.
And cariboo907 i'm sorry to put that in security. Thnx for ur help.....


Thanks people........:)

---

### Post by dcstar on 2010-04-28
Install the **pysdm** package.

Hmmm, be careful with this package, I just found a bug that does not identify all the partitions on one of my drives correctly.

---

### Post by dino99 on 2010-04-28
MountManager is your boy  :P

---

### Post by Morbius1 on 2010-04-28
This is more a compliment to bcbc's post. You are given an opportunity at install time to mount these non-system partitions automatically if you choose the manual partitioning rout. What ubuntu uses as templates look like this ( except they use UUID's instead of /dev/sdxy ):

> /dev/sda1 /media/WinC ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda6 /media/WinD vfat utf8,umask=007,gid=46 0 2
/dev/sdb6 /media/Data ext3 defaults,noatime 0 2I usually modify these a bit but for the most part it's good enough for me.

If you're interested:
The ntfs and Fat32 lines will mount with owner=root and with read / write permissions to all local login users ( the umask=007 / gid=46 part).
The ext3 line will mount with owner=root and with read only access to everyone other than root.

To allow read / write access to those ext3 partitions you need to modify ownership or permissions with a chown or chmod command.

If you decide to go down the pysdm / mountmanager route and then decide that the jedi way is best, I would recommend one modification to bcbc's post:

Instead of:
**sudo blkid**
Use:
**sudo blkid -c /dev/null**

The latter command cleans out the cache and refreshes so you get a more accurate display of the available partitions.

---

### Post by Rong2k on 2010-05-04
There's faster and more flexible way of doing this in ubuntu 10.04

Create a script somwhere:
```

#!/bin/sh
for i in $(udisks --enumerate-device-files | grep -v disk | grep -e [0-9]$)
do
  udisks --mount $i
done

```

Then make it executable by entering in console

```

chmod +x where_you_saved_your_script

```

Add it to Startup Applications in System->Preferences

It will create folders in /media with fancy label-names for every partition on user logon like you mounted them yourself in nautilus.

Also notice that any programs that uses these partitions should be started after running the script. So if you need to run something before user logon, go with fstab. Otherwise add something like that in the script:

```

# Run vuze. Append & for a non-blocking call.
sh /media/V/torrents/vuze/vuze &

```

---

### Post by hirumono on 2010-06-03
> **Rong2k said:**
> There's faster and more flexible way of doing this in ubuntu 10.04

Create a script somwhere:
```

#!/bin/sh
for i in $(udisks --enumerate-device-files | grep -v disk | grep -e [0-9]$)
do
  udisks --mount $i
done

```

Then make it executable by entering in console

```

chmod +x where_you_saved_your_script

```

Add it to Startup Applications in System->Preferences

It will create folders in /media with fancy label-names for every partition on user logon like you mounted them yourself in nautilus.


Thank you very much, Rong2k!!!  :)
After seeing your use of udisks, I experimented with a script mounting my devices in a fixed way, only to find out that under Lucid, device IDs seem to vary with every reboot!!! (i.e. my secondary HD is /dev/sda now, and /dev/sdb the next reboot...) :evil:
In Karmic I used gnome-mount with partition names, and it worked like a charm...  :|
So thank you for helping me auto-mounting my 11 data partitions!!  :mrgreen:

---

