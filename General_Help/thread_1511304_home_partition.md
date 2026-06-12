---
title: "/home partition"
date: 2010-06-16
forum: General Help
---

### Post by Scunnered on 2010-06-16
I thought that I had managed to set up the above but now discover that I am still having a problem.  Using GParted I established the required partition and when I open the Places list I see below Computer a symbol and /home.

Placing the cursor over /home it displays mount /home and it is here that I now have problems.  Clicking on the item shows a lost+found folder with an X. Attempting to open this folder advises "***The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "lost+found***".

I then attempted to copy my previous Home Folder information only to find that the paste facility is greyed out.

What do I need to do now to place my data within the separate /home partition?  Your kind assistance will be appreciated.

---

### Post by jerome1232 on 2010-06-16
You mean like the lost+found on mine? yeah that's normal all partitions get one, fsck sticks partially recovered files there if bad things happen during a disk check.


So it sounds like you just need to copy files over (should've done that before you booted into your install) So my question is exactly how did you backup the files from your original /home?  And did you backup /home or did you backup YOUR USERS home folder (which would be /home/usernamehere)?




So if you backup your entire /home and permissions are intact and all that jazz I would just rsync it from a live cd.


If you have a full blown copy of /home then I would do it like this, you would need to adjust the /dev paths to your real situation. Let me know if you need help figuring that out if you don't already know.
```
sudo -i
mkdir /mnt/home
mkdir /mnt/oldhome
mount /mnt/home /dev/sdx#
mount /mnt/oldhome /dev/sdx#
rsync -av /mnt/oldhome/ /mnt/home
exit
```


Now if you just copied your users home folder somewhere than we need to do it a bit differently. From a live cd again.

```
sudo -i
mkdir /mnt/home
mkdir /mnt/oldhome
mount /mnt/home /dev/sdx#
mount /mnt/oldhome /dev/sdx#
mkdir /mnt/home/<yourusernamehere>
chown 1000:1000 /mnt/home/<yourusernamehere
chmod u=rwx,g=rx,o=rx /mnt/home/<yourusernamehere>
rsync -av /mnt/oldhome/ /mnt/home/<yourusernamehere>
exit

```

Post back if you have any questions before just blindly attempting anything! Don't want to lose your data because of a misunderstanding of some sort!

---

### Post by dabl on 2010-06-16
and maybe this helps too:  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Scunnered on 2010-06-17
My thanks to you both for your assistance.

**dabl**

I had read that link before but obviously not understood it properly. I will take some more time and go around again.  First glance appears to be similar to that offered by jerome.

**jerome1232**

So that I don't mess things up further this is how I tackled the backing up of my data.  Before I established the separate /home partition I copied everything that resided in Places > Home Folder > Ian on to an external hard drive. Thereafter I used the LIVE DVD and created the separate folder.

In my ignorance I thought that all I needed to do was then copy the data over to that folder when it displayed on the places menu list. So much for that theory !

As my data now is stored externally, on a USB connected drive, from the system what do I need to do to place it where it should be.  My Lucid OS is on sda1 and the separate home on sda3 for your info.
 
If you could advise further it will be appreciated.

---

### Post by jerome1232 on 2010-06-17
If you didn't get all your hidden directories, then your missing all of your user defined settings, hidden directories start with a . in front of them, like .wine, just something to be aware of.


So sounds like we need to go with option 2. First from your real install whats the output of this command (with usb drive plugged in)

```
mount
```

---

### Post by Scunnered on 2010-06-17
**jerome1232**

As requested please find output of mount

"ian@ian-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ian)
/dev/sdb1 on /media/500B-A4C0 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)"

I hope this is of assistance

Thanks again

---

### Post by jerome1232 on 2010-06-17
You don't have another partition mounted as /home according to that.

Need more info then (sorry)

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by Scunnered on 2010-06-17
Looks very much like I have gone astray again from your comments.

This is the output from your code requests:

"ian@ian-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=87cadc59-9ef7-40ad-a7c6-ffcdab406e1e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=82d788fc-5242-48a0-a5d4-80904deaf12e none            swap    sw              0       0
ian@ian-laptop:~$ sudo fdisk -l
[sudo] password for ian: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002feda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1298    10426153+  83  Linux
/dev/sda2           19088       19458     2972673    5  Extended
/dev/sda3            1299        7773    52010437+  83  Linux
/dev/sda5           19088       19458     2972672   82  Linux swap / Solaris

Partition table entries are not in disk order"

I trust this assists

---

### Post by Scunnered on 2010-06-17
**jerome1232**

As an afterthought in the hope it assists I attach a screenshot of my partitions.

---

### Post by DCGStudios on 2010-06-17
jerome1232 gave alot of this information already, but it might be good to read this over.. granted you might need to change a few things around since your using an external HD..

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Scunnered on 2010-06-18
**DCGStudios**

Both dabl and yourself directed me to the same item which having re-read takes me part of the way down the road. I can understand from it that I require to effectively transfer the old home to the new partition.  It is this point that I am struggling with as all my data being stored externally I don't know what I need to do to achieve it.

I am wondering that when **jerome1232** stated "*You don't have another partition mounted as /home according to that*" if the fact I am working with a fresh installation is the problem.  All that I have done since the initial install was to adjust minor settings and ensure that the system is fully up to date.  Could the lack of any information in the Home Folder be put down to this.

As a senior citizen my desire to work with Ubuntu & Linux is tempered with my total lack of knowledge of computing and as such is why I throw myself on the mercy of the forum.  

I am hoping to use Lucid as it is a LTS version but wished to be able to see what the developments bring up and it was for this reason that I wished a separate /home.

If you can assist further it would be appreciated

---

### Post by jerome1232 on 2010-06-18
Sorry I started a reply yesterday and got side tracked.

So we'll what we will need to do is this

A) Boot from a live cd

B) Do all of this (explanations will have a # sign in front of them. You may have to modify a few parts for your specific needs (will highlight lines that will need modification in blue, one spot that may need modification is in green, depends on if you put your backups in a folder or not.)

```

# Escalating to root, so we don't have to type sudo constantly :P
sudo -i
# Creating mount points for your partitions so we can do work on them
mkdir /mnt/root
mkdir /mnt/oldhome
mkdir /mnt/home
# The actual mounting
# /dev/sda1 is your root partition
# /dev/sda3 is what I'm assuming is to be your new /home
# /dev/sdb1 is your external drive
mount /dev/sda1 /mnt/root
mount /dev/sda3 /mnt/home
mount /dev/sdb1 /mnt/oldhome
# Creating your user directory
mkdir /mnt/home/[COLOR="RoyalBlue"]<yourusersnamehere>[/COLOR]
# Copying your files from your exteranl drive to the new /home
rsync -av [COLOR="Lime"]/mnt/oldhome/ [/COLOR]/mnt/home/[COLOR="RoyalBlue"]<yourusernamehere>[/COLOR]/
# Setting your user as the owner of all the files in his home directory
chown -R 1000:1000 /mnt/home/[COLOR="RoyalBlue"]<yourusersnamehere>[/COLOR]
# Moving all the old files out of your new installation (since we will be mounting /dev/sda3 there we need to clear the files out leaving an empty directory) You can delete this later if everything works out fine.
mv /mnt/root/home/* /mnt/home/<yourusernamehere>/.backuphome/

# Getting the uuid of /dev/sda3 so we can edit fstab and put it in there
tune2fs /dev/sda3 -l | grep UUID
exit
gksu gedit /mnt/root/etc/fstab
## You want to add a line to this file to get /dev/sda3 mounted during the boot process 
## you need to add the line below

UUID="[COLOR="RoyalBlue"]<copy and paste the big number from the command above>[/COLOR]" /home ext4 defaults 0 2
```

If you have questions feel free to ask, if something fails with an error please post the output (you can get online from a live cd)

---

### Post by Scunnered on 2010-06-18
**jerome1232**

Thanks for your reply.  Your explanations make matters clear and I am starting to see how the process works.

Can I assume that where you mark yourusernamehere that I enter **ian** rather than ian@ian-laptop? 

Where you show in green **/mnt/oldhome/** will need clarification.  When I copied the data that I wished to save on to the USB drive it comprised of two folders.  These were Documents & Photos. The Documents folder was sub-divided into four other folders.

If the way the items have been saved cause problems then just tell me what needs to be done to smooth the transfer.  The Photos folder is only in this instance just to give me different backgrounds and could no doubt be copied from my main external backup later.  The Documents folder is my current active files.

Where you ask that I obtain the UUID seems OK but having got **the big number from the command above** exactly where do I put it. The comment **you need to add the line below** is where I get lost.

Am I right in thinking that once I am using the LIVE CD it should be at this point that I attach my USB drive? 

If you can address the above I will do nothing until I hear further from you.

Again my thanks

---

### Post by jerome1232 on 2010-06-18
Yes you would be typing "ian"


Basically if you were to copy and paste my lines, you would highlight that entire spot highlighted in blue ("copy and paste the big number from above here") and paste the number in it's place.

so it would be (except a different string of letters/numbers) You don't need the quotes around the uuid but I just put them there.

```
UUID="fqb7rgh-fhjkh343j2kl5-5jhj234j" /home ext4 defaults 0 2
```

So to further clarify your entire /etc/fstab file will look like this:
I highlight the line you'll be adding in red, remember the actual uuid will differ based on the output of tune2fs.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=87cadc59-9ef7-40ad-a7c6-ffcdab406e1e / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=82d788fc-5242-48a0-a5d4-80904deaf12e none swap sw 0 0
[COLOR="Red"]UUID="875843850-4243-423423-32423432-324" /home ext4 defaults 0 2[/COLOR]
```

From what you've told me You just backed up your documents and pictures, so let me revise a bit, instead of copying all the files from your external we should copy the files from your current install, then just manually drag your files over. So revised instructions :)

```
# Escalating to root, so we don't have to type sudo constantly :P
sudo -i
# Creating mount points for your partitions so we can do work on them
mkdir /mnt/root
mkdir /mnt/oldhome
mkdir /mnt/home
# The actual mounting
# /dev/sda1 is your root partition
# /dev/sda3 is what I'm assuming is to be your new /home
# /dev/sdb1 is your external drive
mount /dev/sda1 /mnt/root
mount /dev/sda3 /mnt/home
mount /dev/sdb1 /mnt/oldhome
# Doing it this way actually eliminates several steps
rsync -av /mnt/root/home/ /mnt/home/
#### After doing that you should be able to just drag the files over from
#### your regular install, since permissions are all setup correctly and etc via rsync.
#### So let's just worry about getting fstab setup to mount /home at boot time
#### and you can just drag the files in to your new home partition.

# Getting the uuid of /dev/sda3 so we can edit fstab and put it in there
tune2fs /dev/sda3 -l | grep UUID
exit
gksu gedit /mnt/root/etc/fstab
## You want to add a line to this file to get /dev/sda3 mounted during the boot process 
## you need to add the line below

UUID="<copy and paste the big number from the command above>" /home ext4 defaults 0 2
```

Then reboot and drag your files off of the usb disk

---

### Post by Scunnered on 2010-06-18
**jerome1232**

I am very pleased to advise that your instructions were simplicity indeed.

I was able to follow things through to the reboot and was able to copy all my data over from the pen drive. In addition I had a look at my external drive and found that I was also able to copy things again.

My sincere thanks for all your kind assistance.

---

### Post by jerome1232 on 2010-06-18
Glad that worked for you, so just to confirm it worked, when you type 'mount' with no parameters it shows /dev/sda3 as mounted at /home correct?

I did overlook a step (removing the files originally at /home) So if you wanted to clean that up you would just remove them from a live cd again.


[COLOR="Red"]**Do not do this until you are positively sure that /dev/sda3 is in fact mounting as /home during the boot process and your files are in fact on that partition and not on /dev/sda1**[/COLOR], the output of mount will confirm that it's all working
```
sudo -i
mount /dev/sda1 /mnt
rm -rf /mnt/home/*
exit
reboot
```

---

### Post by Scunnered on 2010-06-19
**jerome1232**

Thanks for your reply.

Everything is working totally to plan. 

My sincere thanks for all your kind assistance.

---

