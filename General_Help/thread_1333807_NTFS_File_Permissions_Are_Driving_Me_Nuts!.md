---
title: "NTFS File Permissions Are Driving Me Nuts!"
date: 2009-11-21
forum: General Help
---

### Post by istigkeit on 2009-11-21
Straight to business!

I have installed Ubuntu 9.1 with two users alongside Windows XP on an internal drive. I also have a USB external used primarily for extra storage. Both XP and the external drive are NTFS.

I cannot for the life of me seem to set proper folder permissions for the users on my Ubuntu install. I simply want both users to be able to freely gain access to both drives. What I've done so far:

Mounted the volumes with myself as owner.

Discovered *chmod* is no good in this instance as it doesn't work well with NTFS.

Have had no luck trying *umask* either. I navigated to the location of the external drive, and did various *umask* commands (*umask 057, umask 002, etc*). This appeared to have no effect.

Most strange of all was attempting to manually change the settings. Right-click the volume, click the Permissions tab. Here I would see myself as owner with folder access set to "Create and Delete files," all others set to None.

I can't change these either. If I adjust a setting under the group I want changed (a group with the two users in it), it will switch back to the default None the very moment I click it.

Anything under Group or Others will change back to None the moment I click any other setting. There isn't a chance to click Apply Permissions since I can't select any option.

From here, I'm not sure what else to try.

---

### Post by Zoot7 on 2009-11-21
Ntfs/FAT32 don't support the Linux filesystem's permission by default.

Your best bet if you want permissions set is just to use something like ext3.

---

### Post by istigkeit on 2009-11-21
I don't understand.

Are you saying I can't use Ubuntu and have user access to NTFS file systems? This seems contrary to what I've learned thus far.

---

### Post by Zoot7 on 2009-11-21
Well you can read and write just fine, but as Ubuntu sees the permissions it's 777 ie. read, write and execute for everybody.
You just can't change them.

---

### Post by istigkeit on 2009-11-21
If I have the drive mounted, I **can** read and write fine, but other users cannot.

What can I do about this? I want them available to everyone.

---

### Post by Baelus on 2009-11-21
Looks like a bug in Karmic.

[http://ubuntuforums.org/showthread.php?t=1319047]("http://ubuntuforums.org/showthread.php?t=1319047")

---

### Post by Zoot7 on 2009-11-21
> **Baelus said:**
> Looks like a bug in Karmic.

[http://ubuntuforums.org/showthread.php?t=1319047]("http://ubuntuforums.org/showthread.php?t=1319047")

I would have said play around with the authorizations and see what comes of it, but that throws a spanner in the works. :(

---

### Post by sisco311 on 2009-11-21
> **Baelus said:**
> Looks like a bug in Karmic.

[http://ubuntuforums.org/showthread.php?t=1319047]("http://ubuntuforums.org/showthread.php?t=1319047")

unfortunately that's not a bug, it's a feature. 

@istigkeit

sorry, it's 03:45 here, i will try to find a solution to your problem tomorrow (d'oh... i mean today).

---

### Post by Zoot7 on 2009-11-21
Actually, are the other user accounts that can't read from the drive limited accounts (Not in the Admin Group)?

---

### Post by istigkeit on 2009-11-21
> **sisco311 said:**
> unfortunately that's not a bug, it's a feature. 

@istigkeit

sorry, it's 03:45 here, i will try to find a solution to your problem tomorrow (d'oh... i mean today).

Don't worry and take your time, I lol'd :)

That's too bad about it being a noted bug, I was hoping it was simply my error. :(
There was a script noted in the linked thread, I'll take a look at that and see how it works.

A slow workaround I can do is just to unmount any drives before logging out and letting the other user mount, but that's a bit of a pain in the long term.

Thanks to everyone for the quick responses.

---

### Post by istigkeit on 2009-11-21
> **Zoot7 said:**
> Actually, are the other user accounts that can't read from the drive limited accounts (Not in the Admin Group)?

Yes, the other user didn't appear to be in the admin group, I just added them and will see what happens.

---

### Post by sisco311 on 2009-11-22
You will have to create fstab entries for the partitions.

[list=i]

[*] plug in your external drive

[*] open a terminal (Applications -> Accessories -> Terminal)

[*] and paste this command in it:

```
sudo blkid
```
the output should look like this:

```
...
/dev/sda4: UUID="**4D4F5C871DB99941**" TYPE="ntfs" 
/dev/sdb1: UUID="**8DEF23841B959AD3**" TYPE="ntfs"
...


```
**4D4F5C871DB99941** and **8DEF23841B959AD3** are the UUIDs of the partitions.


[*] backup the fstab file:
```
sudo cp /etc/fstab /etc/fstab-backup
```

[*] edit the file:
```
gksu gedit /etc/fstab
```

[*] add the new entries to the end of the file:

```
UUID=**1234567890ABCDEF**    /media/*internal*    ntfs    defaults,gid=plugdev,dmask=002,fmask=113,users    0     0


UUID=**1234567890ABCDEF**    /media/*external*    ntfs    defaults,gid=plugdev,dmask=002,fmask=113,users,noauto    0     0
``` 

replace **1234567890ABCDEF** with the UUID you get from the *blkid* command,

/media/*internal* and /media/*external* with the name of the directory (mount point) where you want to mount the partitions (i.e. /media/music)

If you don't want to mount the internal partition automatically at boot time, then  add noauto to the mount options:
defaults,gid=plugdev,dmask=002,fmask=113,users,**noauto**

[*] create the mount points:
```
sudo mkdir /media/internal
sudo mkdir /media/external
``` 

[*] mount the partitions:
```
sudo mount -a
```

[/list]

Every user in the plugdev group will have read/write permission on the partitions. To add a user to the plugdev group:
```
sudo adduser **username** plugdev
```
replace **username** with the user's login name.

---

### Post by istigkeit on 2010-01-26
This reply is very late, but nonetheless . . .

Adjustments to fstab as suggested above did exactly what I needed.

Thank you.

---

