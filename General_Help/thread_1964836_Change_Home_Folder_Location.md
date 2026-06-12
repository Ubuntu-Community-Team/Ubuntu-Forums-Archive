---
title: "Change Home Folder Location"
date: 2012-04-24
forum: General Help
---

### Post by Chriske on 2012-04-24
Hi,

When I installed the last Ubuntu release I created a separate partition for the /home folder and this worked fine.

How would I modify Ubuntu now to change the /home folder's location back to the default?

Thank you.

---

### Post by papibe on 2012-04-24
Hi Chriske.

That is a very common practice. I'd even say a good practice. Is there a reason you want to have all in one partition?

Take a look at this [tutorial]("https://help.ubuntu.com/community/Partitioning/Home/Moving") and tell us if you need more help.

I hope that helps.
Regards

---

### Post by Chriske on 2012-04-24
Hi papibe,

Many thanks for the quick reply.

I want to install 12.04 in a separate partition when it is released and have that point to my existing /home partition. But, I'm thinking that if both installations of Ubuntu point to the same /home folder, then there will be some conflicts regarding settings, etc for things like the desktop and, say, Firefox.

So, my thinking was to move the existing settings from the /home partition back to 11.10s default /home folder location.

I'm finding it difficult to follow the guide to do that. 

Thanks.

---

### Post by papibe on 2012-04-24
> **Chriske said:**
> I'm finding it difficult to follow the guide to do that.

Let's try to make it work then.

Could you post the result of these commands?
```
sudo fdisk -l

mount -l

df -h
```
And also paste the content of this file:
```
/etc/fstab
```
Please wrap the results using the code tags (#) available when replying.
Regards.

EDIT: BRB in an hour or so.

---

### Post by oldfred on 2012-04-24
The settings are primarily all the hidden files & folders. I had a separate /home for all of 5 minutes and realized like you that I might have conflicts as I was installing a new clean 64bit version in a new partition to replace my 32 bit version. So I moved all the data folders like Documents, Music, Video etc to a Linux data partition. I already had moved my Firefox and Thunderbird profiles to a shared NTFS partition and my /home was tiny. It grew again but only to just over 1GB with .wine which I have not moved to a separate partition. Since then I just install with /home inside my root and copy some settings (most bits of data) from the old install and relink my data partitions.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Chriske on 2012-04-24
Thanks oldfred. That describes exactly my problem and what I'd like to achieve.

And thank you papibe for the help. Here is what I have:

```

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce48c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    21608447    10803200   83  Linux
/dev/sda2       617019390   625141759     4061185    5  Extended
/dev/sda3        43190272   617017343   286913536   83  Linux
/dev/sda4        21608448    43190271    10790912   83  Linux
/dev/sda5       617019392   625141759     4061184   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f23d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf2       215050240   625141759   205045760   83  Linux
```
```
mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,commit=0) [Home]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
``````
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              11G  4.5G  5.2G  47% /
udev                  1.9G  4.0K  1.9G   1% /dev
tmpfs                 768M 1020K  767M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.9G  400K  1.9G   1% /run/shm
/dev/sda3             270G   83G  174G  33% /home
```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c43c0cf3-02da-4b80-973f-ca953ea1aef3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=1c4bff6f-6c1e-4a08-bdd8-7d931367a3c3 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=4a37ccca-36cb-4118-bc4a-cfbff1197bac none            swap    sw              0       0
```

Off to bed now, so I'll pick up next tomorrow.

---

### Post by ajgreeny on 2012-04-24
As you already have a separate /home partition now, I suggest you keep things as they are at the moment, but in your next install leave the home folder within root. Now by adding a line in the new OS's /etc/fstab,  you can automount the old /home partition to a new /mnt/11-10 folder that you will need to make in the new OS filesystem.

You can then easily make links to the old data folders (Video, Music, Documents, Pictures, etc etc) plus any config folders that you want for both OSs (.mozilla, .thunderbird, etc etc).  Doing this will mean that all configurations are kept separate for each OS, but the data files will be the same for both, but will not be duplicated.

This is exactly what I do at the moment with the 5 different OSs on my main desktop machine, and it all works faultlessly.

---

### Post by papibe on 2012-04-24
There are several ideas on the table.

In the mean time I've noticed that your home does not fit on your root partition. Your current home uses 83G and you only have 5.2GB available.

That means that your original idea can't be done that easily. oldfred and ajgreeny's ideas look like a better solution all around.

This is an example headed on that direction (think it as a first step):
[INDENT]*Move your current home to the root partition. However, just move your configuration files. All your data (music, documents, etc) will be on a different partition so it can be mounted from any Linux version as needed (actually the same partition as it is right now).*[/INDENT]
Create the new home with a temporary name.
```
sudo mkdir /newhome
```
Create your user home directory and change its ownership to you:
```
sudo mkdir /newhome/youruser
sudo chown youruser:youruser /newhome/youruser
```
Copy your configuration files ('cp' will do fine, but I like rsync):
```
rsync -axv --include='.*' --exclude='*' /home/youruser/ /newhome/youruser/
```
Create the mount point for the rest of your files (not using sudo):
```
mkdir /newhome/youruser/Data
```

Then you need to edit your mounting points in /etc/fstab, but first back it up:
```
sudo cp /etc/fstab  /etc/fstab.old
```
Edit your file:
```
gksudo /etc/fstab
```
You need to change just one line. This one:
```
UUID=1c4bff6f-6c1e-4a08-bdd8-7d931367a3c3  /home  ext4  defaults  0  2
```
So it looks like this:
```
UUID=1c4bff6f-6c1e-4a08-bdd8-7d931367a3c3  **[COLOR="Red"]/home/youruser/Data[/COLOR]**  ext4  defaults  0   2
```

Now you are ready to make the switch:
```
cd /
sudo umount /home
sudo mv /home /oldhome
sudo mv /newhome /home

sudo mount -a
```

That's it.

Make sure everything is in place:

Check if your home is available and has your config files:
```
cd ~
la
```
Then check your old data is in the right place:
```
cd ~/Data/youruser
ls
```
You are done! Restart your machine to check if everything is working properly.

Hope that helps, and tell us how it goes.
Regards.

Other notes:

1. The oldhome is doing nothing right now, so you may want to delete it. But check first it is empty:
```
ls /oldhome

sudo rm -rf /oldhome
```

2. I would get your old data one level up so it would be easily accessible:
```
cd ~/Data/youruser
mv -iv * ..
```

3. You probably want to either resize the now Data partition to make space for 12.04 (or may be use the other disk?)

---

### Post by Chriske on 2012-04-25
Thank you so much everybody for your kind help. This is a major reason why I use Ubuntu: the nature of responses on this forum when you need help is outstanding! :p

Thanks papibe for that detailed step-by-step guide, which (of course!) worked like a charm. In fact, it was exactly what I wanted to achieve originally, but I didn't explain myself well. Luckily, oldfred and ajgreeny did that better than I could. I had already resized partitions for that reason.

As I said, your guide worked fine and I now have a "mini /home" with my settings and can still point to /Data whenever I need to. Brilliant!

I had a couple of glitches - probably down to me. I couldn't unmount the original /home from within Ubuntu, so had to reboot and do the switch from a command line via GRUB. Also, when the OS did reboot, I did not have my settings for desktop, Firefox, etc. Rather I had the default settings. But, I simply copied the "hidden" files from /Data, rebooted and all is fine.

Thanks very much once again. =D>

---

