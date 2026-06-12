---
title: "hard-linking /data folders to /home with fstab"
date: 2011-10-23
forum: General Help
---

### Post by akand074 on 2011-10-23
So initially I had / on my SSD and /home on my HDD. I just did a clean install of Oneiric but put my entire filesystem including /home on my SSD and instead had my old /home folder mounted at /media/data. I'm now trying to hard-link the two so that whenever I refer to any of my folders in /home it automatically looks in my /media/data folders seamlessly as if they were the same folder. What I did was put the folders into the correct place and then changed the entire /media/data folder owner to my user. Then I added this to the end of /etc/fstab via gksu gedit /etc/fstab:

```
LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/Documents  /home/andrew/Documents  none  bind  0  0
/media/data/Downloads  /home/andrew/Downloads  none  bind  0  0
/media/data/Music  /home/andrew/Music  none  bind  0  0
/media/data/Pictures  /home/andrew/Pictures  none  bind  0  0
/media/data/Videos  /home/andrew/Videos  none  bind  0  0
/media/data/Public  /home/andrew/Public  none  bind  0  0
```

After I restart it fails to mount the partition so I press "S" to skip and when I log in and try to mount it manually it basically says I can't because it belongs to root. I then remove what I had added to the end of fstab and restart and it boots again and mounts fine (though not hardlinked). Anyone have any clue what may be the problem?

---

### Post by akand074 on 2011-10-23
From a bit of reading, apparently you can't create hard-links between different file systems (and often not even with directories). Though, what I'm trying to do isn't actually a hard-link. I'm actually trying to mount each folder in a different location. Which should be possible even from different hard drives, but I'm not sure. Anyways, in the mean time I've created symbolic links to all the folders.

---

### Post by nothingspecial on 2011-10-24
Basic checks first.

1. The drive is labled Data and is formatted ext4

2. The directory /media/data exists. The automount feature will create the directory /media/DATA when you plug it in. If you mount it with fstab the directory has to exist already.

3. You own the drive.

4. The directories in your /home/$USER exist and are empty.

I have no idea if ssds effect any of this because I have never used one.

---

### Post by akand074 on 2011-10-24
> **nothingspecial said:**
> Basic checks first.

1. The drive is labled Data and is formatted ext4



I just copied what you had in your fstab and changes the folders to mine. I didn't distinctly label a drive Data or made any changes. 


> **nothingspecial said:**
> 2. The directory /media/data exists. The automount feature will create the directory /media/DATA when you plug it in. If you mount it with fstab the directory has to exist already. 

The folder already exists with all the sub folders I wanted mounted within /home

> **nothingspecial said:**
> 
3. You own the drive.


I right clicked /media and changed it's owner to my user along with all enclosed files and folders. If I right click /media/data it says my user owns it. Is that what you mean?

> **nothingspecial said:**
> 
4. The directories in your /home/$USER exist and are empty.

I have no idea if ssds effect any of this because I have never used one.

They do exist and are empty, though currently they are actually just folders with a symbolic link to the folders in /media/data but that can easily be reverted.

---

### Post by oldfred on 2011-10-24
I just use soft links and only mount the data partition in /mnt/data.

But bind is supposedly a better way. Your SSD may mount too fast for HDD to mount with the bind. Then you may want an upstart script.

Another way to share:
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

---

### Post by Morbius1 on 2011-10-24
@oldfred, thanks for the plug but I think bindfs is going to have the same problem as a normal bind in fstab. I thinks it's a timing issue. I would go with the upstart idea:

[1] Create an upstart script named "home-mounts.conf"
```
  gksu gedit /etc/init/home-mounts.conf 
```[2] The content of that file would look something like this:
```
# Remount partitions with bind
#
description "Bind Data Subdirectories to Andres' Home Directory"

start on stopped mountall

script
mount --bind /media/data/Documents  /home/andrew/Documents
mount --bind /media/data/Downloads  /home/andrew/Downloads
mount --bind /media/data/Music  /home/andrew/Music
mount --bind /media/data/Pictures  /home/andrew/Pictures
mount --bind /media/data/Videos  /home/andrew/Videos
mount --bind /media/data/Public  /home/andrew/Public
end script
```It's the "start on stopped mountall" that does the trick since it won't run the script until everything in fstab ( i.e., /media/data ) is mounted first.

---

### Post by nothingspecial on 2011-10-24
> **akand074 said:**
> I didn't distinctly label a drive Data or made any changes. 


While I bow to the vastly superior knowledge of oldfred and Morbius1.....

if your drive is not labeled Data the whole thing will fail.

---

### Post by akand074 on 2011-10-24
> **nothingspecial said:**
> While I bow to the vastly superior knowledge of oldfred and Morbius1.....

if your drive is not labeled Data the whole thing will fail.

I see. I'm going to give Morbius1's route a go a little later perhaps. Thanks for the help!

Yeah when I first got my SSD I had a lot of problems where the OS was loading faster than the config files in /home and would thus load with an odd look. It also used to hang a bit on boot. With oneiric now having /home on the SSD I've had no problems and my boot time dropped significantly. Under 15 seconds now it seems. 

Anyways, I'll give that script a go. Worst case, the soft links do the job fine, I would though preferably like to not have the HDD show up in devices and be able unmount it (might eject it by accident) but it's not the end of the world.

---

### Post by dcstar on 2011-10-25
> **oldfred said:**
> I just use soft links and only mount the data partition in /mnt/data.

But bind is supposedly a better way.
.......

A matter of opinion, apparently:

[http://www.fedoraforum.org/forum/showthread.php?t=150277](http://www.fedoraforum.org/forum/showthread.php?t=150277)

And this is worth a peruse:

[http://aplawrence.com/Linux/mount_bind.html](http://aplawrence.com/Linux/mount_bind.html)

---

### Post by Morbius1 on 2011-10-25
> **nothingspecial said:**
> While I bow to the vastly superior knowledge of oldfred and Morbius1.....

if your drive is not labeled Data the whole thing will fail.
I missed that in this thread. So much for "vastly superior knowledge" ;)

You can get around this problem by not using LABEL in fstab but do it by UUID. So instead of this:
>  LABEL=Data  /media/data  ext4  defaults  0  0It becomes this:
> UUID=e92eaf02-ff61-4db0-9397-35f1aadb98e8  /media/data  ext4  defaults  0  0TO find the correct UUID for you partition run the following command:
```
sudo blkid -c /dev/null
```

---

### Post by MagicThinker on 2011-10-25
G'day

I use:   sudo mount -a when making changes to fstab 
The changes then take into effect immediately without needing to reboot.  Also from experience make a backup copy of the fstab file before making too vast changes.

Utilise the partitions UUID's so that the correct partition/s of your device are mounted, it makes doing what you are attempting to do much much much easier.
(I use flash card and SDD devices all the time so the old /dev/sdb and /dev/sde,  etc makes the system unstable when constantly inserting different HOT SWAPABLE drives)


Step 1> Command is:  sudo blkid -o value -s UUID dev/sdd   (replace the /dev/sdd with where ever it gets automounted if it is a flash device)

This will give you a unique UUID for the drive/partition.

use this value in Step 3


Step 2> Make sure that the Target mount directory have been created or is there to mount it on  (sudo mkdir /media/data)

Step 3> In fstab add the value from step 1

normally in the form:  UUID=########-####-####-####-############  /media/data	defaults	0	2

As long as you have applied the permission to yourself for /media/data after it have been mounted via the fstab file you will own the drive and anything onit.

( chown -Rv u+rwx user:user /media/data ) (the -R will apply the same permissions all of the directoires/sub directories )


Step 4>  sudo mount -a  (Use this to remount the devices mentioned in the fstab file)

Step 5>  navigate to /media/data

Step 6> sudo ln -s /media/data/Documents /home/andrew/Download
also make sure that the directories that you are creating links to such as /home/andrew/Downloads does not exist or rename it if it does.  As the linking will give an error saying that the target location has a file name /home/ ... exist and cannot create link.  I always check the folders that I am creating links into and rename the directories if they already exist, this ensures no data loss.


I have been doing this simple method for the past 5 years with all of the difference verisons of UBUNTU with FAT32 NTFS, EXT3 EXT4 makes no difference as you are only linking to a already mounted file system.  If you don't have the drive in the machine as is the case with a HOTswappable removable drives no problem
on bootup skip the error and manually mount the fstab file once you have the drive in the machine.  As these are only links they will only be valid when the media if mounted else it will point to an empty space in /media/data.

If you use the UUID of the drive it wont matter if you use a SDD, HDD or other flash media as it will be based on the unique id of the drive unless of course you clone the drive in which case you will also clone the UUID.


Cheers hope this helps.

---

### Post by MagicThinker on 2011-10-25
This is a good forum.

---

### Post by Morbius1 on 2011-10-25
This symlinks vs bind debate really ends up depending on how you use your machine. 

If you use any kind of file sharing mechanism like Samba, Apache ( I think) , or even "Personal File Sharing", ( I don't know about NFS ), symlinks simply won't work. The remote client is not allowed to followi symlinks. In the case of Samba there's a way around this but Samba considers it a security problem. A bind doesn't have this problem.

If you don't plan on sharing any of these directories across the lan then symlinks are fine.

[COLOR=Blue]EDIT[/COLOR]: I haven't used NFS in about a decade so this might be totally inaccurate but I think the nfs client sees the symlink relative to his own system not the servers so the symlink will point to a directory that doesn't exist on his system.

---

### Post by oldfred on 2011-10-25
I use NFS to connect my two Linux boxes occasionally. But I use a script to mount the fstab entries as mounts not the symlinks. First time I just assumed the symlinks would not work but did not see an issue as I am mounting the fstab entry.

Mount laptops /mnt/data in destop:

sudo mkdir /mnt/data_LT
sudo mount 192.168.1.120:/mnt/data /mnt/data_LT

this is part of my script for every new install:
#NFS setup
fname_exp=/etc/exports
nfs1="/mnt/data 192.168.1.0/24(rw,no_root_squash,async)"
nfs2="/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp

---

