---
title: "&quot;Place&quot; to mount 2nd partition; how can I change the mount command?"
date: 2010-07-27
forum: General Help
---

### Post by henrylaw on 2010-07-27
Lucid 64-bit desktop just installed and updated.  The machine has a second drive formatted VFAT with the label "D-DISK".  There's an entry in "Places" called "D-DISK" which mounts this second drive on /media/D-DISK.  That's fine, but to help my windows users I'd like to change the mount point, probably to /d, so instead of D:\foo\bar they now have /d/foo/bar, which they might find easier.

How do I edit the "mount" command that presumably underlies that "Place"?  

I've tried right clicking and editing bookmarks and not found it.

---

### Post by rubylaser on 2010-07-27
You'll need to make an entry in /etc/fstab to change the mount point.  Or you could use a GUI like this if you have Gnome running on the box.
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

Here's an /etc/fstab line for you (obviously change the UUID to match your drive...
```
UUID=12102C02102CEB83  /media/windows  vfat auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

Here's how you get your UUID
```
sudo vol_id -u /dev/sda2
``` Where sda2 is the drive and 2 is the partition number.

Hope that helps.

---

### Post by Morbius1 on 2010-07-27
Or you could do this:

Create the "d" mount point:
```
sudo mkdir /media/d
```Add a line to fstab:
```
LABEL=D-DISK /media/d vfat utf8,umask=007,gid=46 0 2
```You might want to verify that the LABEL is correct by using this command:
```
sudo blkid -c /dev/null
```umask=007 will give owner (root) and group read / write access.
gid=46 is the plugdev group. All local login users are members of the plugdev group
So all local login users will have read / write access to the partition.

NOTE: I would avoid using the "users" option as that will give any user the ability to unmount the partition.

---

### Post by typal on 2010-07-27
The above should work, but instead of /media/windows, I'd use /home/[user]/d as the mount point.  Make sure to create a /d folder in your home folder with 
```
cd ~
mkdir d
```
Then remount your partitions to see if it worked with
```
sudo mount -a
```

---

### Post by Morbius1 on 2010-07-27
Too may cooks spoiling this broth, I'm out of here :p

Good luck.

---

### Post by henrylaw on 2010-07-27
Thank you all; what an interesting and useful set of suggestions.  Yes, lots of cooks, but that's Linux for you.  I'm only a sous chef myself, but good enough to take what you've suggested and cook it up.

I particularly like the idea of having the FS mounted on ~/d as seen by the user; I think that would be easy to understand.

---

