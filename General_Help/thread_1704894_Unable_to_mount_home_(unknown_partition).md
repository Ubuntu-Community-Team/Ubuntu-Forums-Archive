---
title: "Unable to mount /home (unknown partition)"
date: 2011-03-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-11
all of a sudden i am not able to mount it during boot
nothing was done out of the ordinary
i am on a live cd now
it is a ext4 partition
any ideas?

---

### Post by pqwoerituytrueiwoq on 2011-03-11
anyone have any idea how to recover it?
i don't want to have toe tell my girlfriend she has to re-rip all her cds (over 100) and re-do all her firefox settings (most of which i helped with)

---

### Post by r.osmanov on 2011-03-11
What is in */etc/fstab*? Did you try *System-Administration-Disk Utility*?

---

### Post by pqwoerituytrueiwoq on 2011-03-11
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fc21c0da-7260-407d-8b21-b176df80e3c2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7af4f5da-f7e1-47fa-9cd4-200459159403 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=4ba21645-b193-440f-96f5-b5a90c7ac9ed none            swap    sw              0       0
#firefox
firefox /home/dia/.mozilla/firefox/rhvvc606.default tmpfs size=125M,noauto,user,exec,uid=1000,gid=1000 0 0

```

---

### Post by r.osmanov on 2011-03-11
Well, what about [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)?
Some time ago I successfully recovered data from *reformatted* partition.

---

### Post by oldfred on 2011-03-11
Testdisk would probably be my second choice. I might try this first.


From liveCD so everything is unmounted,swap off if necessary, change sda5 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

---

### Post by tredegar on 2011-03-11
It would be a good idea to run **fsck** on /dev/sda5 before you go any further, and see what that says:

```
sudo  fsck.ext4  /dev/sda5
```

---

### Post by pqwoerituytrueiwoq on 2011-03-11
> **tredegar said:**
> It would be a good idea to run **fsck** on /dev/sda5 before you go any further, and see what that says:

```
sudo  fsck.ext4  /dev/sda5
```
```
 ubuntu@ubuntu:~$ sudo  fsck.ext4  /dev/sda5
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>?
```should i continue with yes?
i am not taking any chances

```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Bad magic number in super-block while trying to open /dev/sda5
/dev/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by r.osmanov on 2011-03-11
I'd make what *oldfred* writes:
```
$ sudo e2fsck -C0 -p -f -v /dev/sda5
```
Then if *e2fsck* fails, I think *TestDisk* is very good option.

---

### Post by jerome1232 on 2011-03-11
If you have external storage you could use dd to make a byte for byte image of the partition and run your fsck's on that image without risk of destroying your original data.


If you fix the image then you can use dd to write the fixed image back to the device.

---

### Post by pqwoerituytrueiwoq on 2011-03-11
> **jerome1232 said:**
> If you have external storage you could use dd to make a byte for byte image of the partition and run your fsck's on that image without risk of destroying your original data.


If you fix the image then you can use dd to write the fixed image back to the device.
sadly this is not an option wish it was

---

### Post by pqwoerituytrueiwoq on 2011-03-11
> **r.osmanov said:**
> I'd make what *oldfred* writes:
```
$ sudo e2fsck -C0 -p -f -v /dev/sda5
```Then if *e2fsck* fails, I think *TestDisk* is very good option.
how would i go about using it?
i extracted it and made it executable
can it fix it with out a separate disk?

---

### Post by tredegar on 2011-03-11
**testdisk** is not an option unless you have somewhere for it to save the recovered files.

Taking a **dd** image of the corrupted partition is also a good idea, but not an option if you have nowhere to save the image.

Perhaps let **fsck** do its thing, using an alternative superblock if that is what it suggests.

---

### Post by oldfred on 2011-03-11
You can try the back up:

List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by pqwoerituytrueiwoq on 2011-03-11
under the assumption it is not recoverable wish fsck how would i go about recreating a home partition?

---

### Post by jerome1232 on 2011-03-11
If you wanted to recreate it over the old one, just use gparted to crate an ext4 filesystem. Then find uuid and update your fstab.


To find the uuid:

```
sudo tune2fs -l | grep UUID
```

Then run

```
gksu gedit /etc/fstab
``` and update the section that says home /dev/sda5 and change the UUID section to match the new uuid.


edit: I'd guess you'd have to recreate at least your users home directories along with permissions, I'm not certain how much/little will be auto-generated when you log in.

---

### Post by pqwoerituytrueiwoq on 2011-03-15
decoded to go with this 
sudo e2fsck -C0 -p -f -v /dev/sda5
it gave me a strait error message this time
sudo e2fsck -f -y -v /dev/sda5
ran that command and it was fixed :)

---

### Post by jerome1232 on 2011-03-15
Glad you were able to get it fixed without losing the data!

---

### Post by pqwoerituytrueiwoq on 2011-03-16
> **jerome1232 said:**
> Glad you were able to get it fixed without losing the data!
Now for the bigger question. Why did it happen in the first place?
will probably never know
*idea wonder what is in the log files*

---

