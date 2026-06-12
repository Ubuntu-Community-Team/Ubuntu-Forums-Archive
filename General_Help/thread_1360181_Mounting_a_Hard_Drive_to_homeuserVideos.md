---
title: "Mounting a Hard Drive to /home/user/Videos"
date: 2009-12-20
forum: General Help
---

### Post by ZER01NE1NE on 2009-12-20
Hello,

When I installed Ubuntu I mounted /usr, /var, /tmp, and /home to their own partitions. Now I'm trying to mount a second hard drive to the Videos folder in my home folder, so I added an entry to fstab. But now it shows the icon on the desktop like it would if I mounted it in the /media folder. And when I look at the icons for the Documents/Downloads/etc. folders in the "Places" menu, the Videos folder shows up like a hard drive. The partitions for /usr and the others don't do that. Is there any way to mount the hard drive a little more seamlessly?

Here's the contents of my fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=bc4da346-233a-479d-a88f-3df4aacc9a1f /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=7584a6e7-f000-417e-b4a1-3af03d16b906 /home           ext3    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=c2dcbc49-de16-4286-9a81-837e268ab4f9 /tmp            ext3    defaults        0       2
# /usr was on /dev/sda5 during installation
UUID=763d8a10-8906-41a9-9461-d384fe14231c /usr            ext3    defaults        0       2
# /var was on /dev/sda6 during installation
UUID=6d8520e4-1df9-44ad-be05-a44dc87fd63c /var            ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=af265325-0e06-48cc-91af-4e5fa8c2506a none            swap    sw              0       0

##############################
# Here's the entry to mount the second hard drive
UUID=fabce297-7674-49bc-9bd5-4ae3a3c7f714 /home/kyle/Videos      ext3      defaults       0      3
##############################

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```Thanks in advance.

~ Kyle

---

### Post by dcstar on 2009-12-20
> **ZER01NE1NE said:**
> Hello,

When I installed Ubuntu I mounted /usr, /var, /tmp, and /home to their own partitions. Now I'm trying to mount a second hard drive to the Videos folder in my home folder, so I added an entry to fstab. But now it shows the icon on the desktop like it would if I mounted it in the /media folder. And when I look at the icons for the Documents/Downloads/etc. folders in the "Places" menu, the Videos folder shows up like a hard drive. The partitions for /usr and the others don't do that. Is there any way to mount the hard drive a little more seamlessly?

Here's the contents of my fstab file:

```

........
# Here's the entry to mount the second hard drive
UUID=fabce297-7674-49bc-9bd5-4ae3a3c7f714 /home/kyle/Videos      ext3      defaults       0      **3**


```

Successful mounts require correct parameters in the fstab file, if you use an incorrect parameter then it will not mount - "3".

If you do not know exactly what you are doing, use a tool like the **pysdm** package to do it correctly.

---

### Post by ZER01NE1NE on 2009-12-20
No, it mounts just fine and I can access the files but it puts this annoying icon on my desktop, I'm trying to figure out how to fix that.

---

### Post by oldfred on 2009-12-20
I put my data partition else where so I do not always see it and linked to it in my /home. I mount my shared partition directly to /home.

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

So I can reuse it in other operating systems or reinstalls. ( have to remove the current directories while they still are empty)
#!/bin/bash
# link data partition to /home
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
ln -s /usr/local/fred/data/Videos
ln -s /usr/local/fred/data/Downloads
ln -s /usr/local/fred/data/PDF
ln -s /usr/local/fred/data/Projects
ln -s /usr/local/fred/data/ISO
ln -s /usr/local/fred/data/eclipsetrader
ln -s /usr/local/fred/data/gnu
ln -s /usr/local/fred/data/itrade
ln -s /usr/local/fred/data/kmymoney
ln -s /usr/local/fred/data/PicasaDocuments
ln -s /usr/local/fred/data/google-earth

edit:
I also had to create the mount point in usr/local and chown the directory

---

### Post by ZER01NE1NE on 2009-12-20
OK, you guys don't seem to get it. I know how to mount a device to a folder and look at the files inside. What's bothering me is that this stupid little icon keeps showing up on my desktop which links to the hard drive mounted to /home/kyle/Videos. My /home, /usr, /var, and /tmp partitions don't do that. How do I get rid of this stupid icon?

~ Kyle

---

### Post by oldfred on 2009-12-20
Do you mean the grey rectangle with the triangle on top? I think that is just to say it is already mounted. If you do not mount in default locations like I do with my data directory you do not see that mount in places at all. I do see the shared directory I mount in home listed in places with the icon.

---

### Post by ZER01NE1NE on 2009-12-20
No. There's an icon on my desktop that looks like a hard drive and says "Video" on it (that's the label of the volume.) When I double click that it takes me to /home/kyle/Videos, which is where I mounted it. I need to know how to get rid of this stupid thing. It's not a big deal if I can't, but it's bugging the hell out of me.

---

### Post by oldfred on 2009-12-20
Again the drives I mount in Media or home are on my desktop. I do not see a big deal. But the drive I mount /usr/local/fred/data does not appear anywhere except as the directories I have linked into my /home.

---

### Post by ZER01NE1NE on 2009-12-21
OK then. It was worth a try I guess.

---

### Post by Morbius1 on 2009-12-21
Partitions mounted in /home or /media end up with an icon on the desktop. Partitions mounted in /mnt or / do not. 

What you could do is mount the second drive to /mnt and then "bind" it to Video :

First, create a new mount point and change your fstab entry for the new drive: For example the new mount point could be newdrive.

 **UUID=fabce297-7674-49bc-9bd5-4ae3a3c7f714 /mnt/newdrive      ext3      defaults       0 2    **

Then right after that entry in fstab add another one to bind /home/kyle/Videos to /mnt/newdrive:

**/mnt/newdrive /home/kyle/Videos auto bind 0 0**

You may have to play with permissions a bit to get the desired result.
I do this for specific directories within a partition but it should work for the whole partition.

---

### Post by Morbius1 on 2009-12-21
Of course you could also stop at this point:

> **UUID=fabce297-7674-49bc-9bd5-4ae3a3c7f714 /mnt/newdrive      ext3      defaults 0 2     **Go to /mnt/newdrive in Nautilus, bookmark it so it shows up under "Places" and rename it to Videos. ;)

[COLOR=RoyalBlue]EDIT: In your original fstab entry the last few options read as this: "defaults 0 3". There is no "3", only 0,1, and 2. So I modified it ( once I finally saw it ) to "2"[/COLOR]

---

