---
title: "Cannot change permission on mounted ntfs disk"
date: 2009-07-05
forum: General Help
---

### Post by elitefox on 2009-07-05
This is the first time I had experience this, I installed ubuntu hardy dual boot with windows xp and I have a problem with changing the permissions on the ntfs disk. The user owning the disk is root and all permissions are set to 555 meaning I cannot delete or write any file onto that disk via gui.

I am trying to change permissions via command line to 775 on any of that disk but failed. Its hard to delete many files at the same time in the command line and I cannot encourage my family to use it if they cannot edit their files on the ntfs volume.

What to do?
--> Is there anything wrong with sudo chmod 775 /media/disk
            *note: there is no error but there is no effect
--> Change the ownership to my username?

---

### Post by elitefox on 2009-07-05
Really Annoying... I am already in the sudoers and root group

---

### Post by diablo75 on 2009-07-05
You might trying running Nautilus as root and then right-click>Properties>Permissions to see if you can change the owner of the files in question to yourself instead of root.

```
sudo nautilus
```

---

### Post by mhgsys on 2009-07-05
> **diablo75 said:**
> You might trying running Nautilus as root and then right-click>Properties>Permissions to see if you can change the owner of the files in question to yourself instead of root.

```
sudo nautilus
```

make that 
```

gksudo nautilus

```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by elitefox on 2009-07-05
> **diablo75 said:**
> You might trying running Nautilus as root and then right-click>Properties>Permissions to see if you can change the owner of the files in question to yourself instead of root.

```
sudo nautilus
```

nope cannot change permission via property since owner is root.


```
gksudo nautilus
```

wow didn't know this is graphical sudo :D 
however this what happen "The permissions could not be determined" Odd, as I said this is the first I have experience this.[IMG]http://i43.tinypic.com/2qnuur5.png[/IMG]

My previous installations gutsy, I can manipulate the data from my xp volume, but for hardy, I don't know what happen :lolflag:

Now I guess I will try to own the disk(my username instead of root), hope there won't be anything go with my xp box, not that I want xp but just programs that me and my family use :D

---

### Post by Nevart on 2009-07-05
Assuming it is a disk created in Windows and not Linux, it is most likely that Windows file and folder permissions is activated, in which case you may be prevented by the "security" in Windows. You might need to go to the root folder in Windows (logged in as administrator in Win) and reset permissions to "Everyone" (Read, Write, Execute).

Then try again in Linux.

---

### Post by elitefox on 2009-07-05
> **Nevart said:**
> Assuming it is a disk created in Windows and not Linux, it is most likely that Windows file and folder permissions is activated, in which case you may be prevented by the "security" in Windows. You might need to go to the root folder in Windows (logged in as administrator in Win) and reset permissions to "Everyone" (Read, Write, Execute).

Then try again in Linux.

:lolflag: didn't know that there is that kind of security available in windows

I'll try, where can it be? Control Panel?

---

### Post by drs305 on 2009-07-05
I think the problem you are running into is that NTFS does not handle permissions as ext2/3/4 filesystems do. Permissions are set at the time of mounting and can't be changed.

To mount the partition so that everyone can access it, assuming you are user 1000, mount it from the command line as below. The uid/gid are your user/group id's, the "umask=000" allows anyone to access the files. Change the device (sdXX) and mount point to one that currently exists:
```

sudo umount /dev/sdXX  # Unmount the device
sudo mount /dev/sdXX /media/mountpoint -t ntfs -o uid=1000,gid=1000,umask=000

```

You can also put this into fstab. This is a good link for the format:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by elitefox on 2009-07-05
> **drs305 said:**
> I think the problem you are running into is that NTFS does not handle permissions as ext2/3/4 filesystems do. Permissions are set at the time of mounting and can't be changed.

To mount the partition so that everyone can access it, assuming you are user 1000, mount it from the command line as below. The uid/gid are your user id, the "umask=000" allows anyone to access the files. Change the mount point to one that currently exists:
```

sudo umount /dev/sdXX  # Unmount the device
sudo mount /dev/sdXX /media/mountpoint -t ntfs -o uid=1000,gid=1000,umask=000

```

You can also put this into fstab. This is a good link for the format:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

@nevart
Just rebooted to xp to find that enable to all, but no luck

@drs305
ok I'll try that, will reboot now to my ubuntu box ):P

---

### Post by Nevart on 2009-07-05
To disable permissions globally you would go to control panel, but I don't recommend that for obvious reasons.  To just do it for the disk, you would simply open an explorer window and right-click on the disk, select properties and then permissions.  You just put a checkmark in "Everybody" and grant all permissions to do anything on the disk.

Even when you actually manage to mount the disk in Linux, you may find that "root" has taken over the disk, and in Ubuntu that can make things a bit tricky. 

What you'll probably find is that it goes from being "unable to determine permissions" or whatever to it just saying that "root" is in charge and the options to do anything are grayed out.

---

### Post by elitefox on 2009-07-05
Thanks to all, especially to drs305 for the fstab and nevart for the windows permission

Albeit I am happy with fstab, so that means that ubuntu change its way of automounting on gutsy and hardy, probably with security reasons.

I am very happy now

---

### Post by elitefox on 2009-07-05
To summarize(might help somebody)

first unmount it
sudo umount /dev/sdXX

make a folder where it will mounted on
sudo mkdir /media/Windows

get the uid of the partition
sudo blkid

backup the /etc/fstab which be configure later
sudo nano -Bw /etc/fstab then press Ctrl+O and Ctrl+X or just cp it

edit the fstab
sudo gedit /etc/fstab

add the following lines
# /dev/hda1 (this is just for comment)
UUID=12102C02102CEB83  /media/windows  ntfs-3g  auto,users,uid=1000,gid=1000,umask=000,fmask=137,utf8  0  0

Many thanks again to drs305

---

### Post by elitefox on 2009-07-06
How do I mark this solve?

---

### Post by drs305 on 2009-07-06
> **elitefox said:**
> How do I mark this solve?

At the lower right of the last post there is an "Edit tags" button. Hit that, then in the middle there is an "Add tag" window where you can add "Solved" as a tag. Then press "Save changes". Anyone can add a tag, by the way, although I would think normally the OP should be the one to mark a thread 'solved'.

---

