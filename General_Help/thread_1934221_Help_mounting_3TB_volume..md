---
title: "Help mounting 3TB volume."
date: 2012-03-01
forum: General Help
---

### Post by errornumber419 on 2012-03-01
I have a 3TB drive which has a 2.73TB ext4 partition on it. I want to use this as a data drive, NOT a boot drive.

I used gdisk to create the filesystem and I then used GParted to make it ext4. But, it will not mount!

If I look at the drive through GParted I see the ext4 partition (which for some reason says it has 44GB used when it should be blank). It is showing as /dev/sdb1.

When I run ```
sudo mount /dev/sdb1 /mnt
``` or ```
sudo mount /dev/sdb1 /media
``` all I get is a new command line and no feedback, no volume being mounted, no new directories in /dev/mnt or /dev/media.

Kind of a linux noob so any help would be awesome!

---

### Post by errornumber419 on 2012-03-01
Sorry, I forgot to mention:


Release: Ubuntu 11.10 (oneiric)
GNOME: 2.32.1
Kernel: 3.0.0-16-generic

---

### Post by GWBouge on 2012-03-01
mount won't make a new directory for the mount, the commands you are using are trying to mount the drive to /media or /mnt directly (which I'm not even sure if that's allowed ...).  If the drive is blank (no files or subfolders), then there is nothing to show in those directories even after it's mounted.

You should create a new folder in /media to mount it:

```
sudo mkdir /media/MyBigDrive
sudo mount /dev/sdb1 /media/MyBigDrive
```

Can you navigate to the drive in Nautilus?

---

### Post by WorMzy on 2012-03-01
> **errornumber419 said:**
> When I run ```
sudo mount /dev/sdb1 /mnt
``` or ```
sudo mount /dev/sdb1 /media
``` all I get is a new command line and no feedback, no volume being mounted, no new directories in /dev/mnt or /dev/media.

Those commands will mount the filesystem at /mnt or /media respectively; it won't create a new subdirectory under those folders for the mount, it will literally mount onto the folders specified. If you haven't created any files or folders on the filesystem yet, then you may not see anything on them (except possibly a lost+found folder). Check the output of ```
mount
``` to check whether the filesystem has mounted or not.

---

### Post by errornumber419 on 2012-03-01
> **GWBouge said:**
> mount won't make a new directory for the mount, the commands you are using are trying to mount the drive to /media or /mnt directly (which I'm not even sure if that's allowed ...).  If the drive is blank (no files or subfolders), then there is nothing to show in those directories even after it's mounted.

You should create a new folder in /media to mount it:

```
sudo mkdir /media/MyBigDrive
sudo mount /dev/sdb1 /media/MyBigDrive
```

Can you navigate to the drive in Nautilus?

> **WorMzy said:**
> Those commands will mount the filesystem at /mnt or /media respectively; it won't create a new subdirectory under those folders for the mount, it will literally mount onto the folders specified. If you haven't created any files or folders on the filesystem yet, then you may not see anything on them (except possibly a lost+found folder). Check the output of ```
mount
``` to check whether the filesystem has mounted or not.

That helped a LOT.

Now if I use:

```
sudo cp -r /media/Backup/Movies/* /media/Movies
```

This should copy the contents of my USB storage at /media/Backup/Movies (recursively) onto my fresh ext4 partition at /dev/sdb1 (which is mounted at /media/Movies/) correct?

---

### Post by jerome1232 on 2012-03-01
Yes, although you should take ownership of the volume and then us cp without sudo.

```
sudo chown -R $USER:$USER /media/Movies
```

edit: making more typos than i can count on one hand today...

---

### Post by errornumber419 on 2012-03-02
> **jerome1232 said:**
> Yes, although you should take ownership of the volume and then us cp without sudo.

```
sudo chown -R $USER:$USER /media/Movies
```

edit: making more typos than i can count on one hand today...

Thanks a lot, that worked great!

And will I need to mount and take ownership of these every time I reboot?

---

### Post by jerome1232 on 2012-03-02
> **errornumber419 said:**
> Thanks a lot, that worked great!

And will I need to mount and take ownership of these every time I reboot?

mount: yes and no

Ownership: One time thing


If you want it to auto mount, you need to setup an fstab entry

Here is a guide about that, first introduces a gui that can do the work for you (probably preferred) then goes on to talk about doing it yourself (if you want to do that)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by jerome1232 on 2012-03-02
I'm just blathering nonsense at this point, I think I'll go have breakfast and come back.

---

### Post by aeiah on 2012-03-02
if you're copying a lot of data, and/or copying it often, consider using rsync instead of cp. it resumes copying and only copies stuff that is different
```

rsync -aP /media/Backup/Movies /media/Movies

```

it isn't quite as fast, but its nice seeing things whizz by and you can stop and start it as you wish :p

---

