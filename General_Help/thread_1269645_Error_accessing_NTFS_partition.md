---
title: "Error accessing NTFS partition"
date: 2009-09-18
forum: General Help
---

### Post by kasl33 on 2009-09-18
I've been having a hell of a time lately getting stuff to run correctly on my new laptop. It's a Dell Inspiron 1440 which came with Vista (I'd have bought the open source Ubuntu laptop, but the hardware specs and price of the Vista one were better and I can get Ubuntu anywhere obviously).

So, after battling ALSA for a few days and finally getting my sound to work (after manually compiling ALSA 1.21), I tried to access my NTFS partition with Vista so that I could get my resume and send it to a company for hopes of getting a job. When I tried to open my Vista partition, I was greeted with the following:

Unable to mount 52.4 GB Media
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Now I have seen other people that have this problem and they blamed it on a specific kernel - 2.6.28-15 (was one instance) but I have tried 2.6.28-11, -14, -15, and am now on 2.6.30 (for graphics reasons - much better!) but still have no access to my NTFS partition.

I have installed NTFS-3g but I'm not quite sure what to do with it quite yet.

---

### Post by carl4926 on 2009-09-18
Post the contents of /etc/fstab

ntfs partitions work well like this:

eg:

```
/dev/sda1    /Vista    ntfs-3g    defaults    0 0
```

The part you are interested in is ntfs-3g defaults 0 0
The first part may be different

---

### Post by kasl33 on 2009-09-18
You're right. The drive wasn't mounted. That's really strange considering before I updated ALSA that it mounted just fine and automatically.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e9bd7d21-20b7-43e4-a2a7-0a6eef115df5 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=af1519e4-e9a1-47af-a1e9-41ae1cf85a2d /home           ext4    relatime        0       2
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

***UPDATE***

For the others who have run into this same problem, here is what I did to get it working (thanks Carl!):

Do this:

gksudo gedit /etc/fstab

Add this to the bottom:

/dev/sda1    /Vista    ntfs-3g    defaults    0 0

Ran this command:

sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /Vista

And now we're in business.> 

---

