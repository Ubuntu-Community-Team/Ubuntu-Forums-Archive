---
title: "How to use Gparted to expand &quot;boxed in&quot; partition?"
date: 2012-04-23
forum: General Help
---

### Post by dishbert on 2012-04-23
I need to expand my main Ubuntu EXT4 partition but it is surrouned (as viewed with the Gparted GUI) by other partitions.  I have created some unallocated space, but that is 3 partitions to the left of the one I need to expand.  I am nervous about deleting and creating partitions as I have had major booting problems after doing this in the past.

Attached is a screen shot of Gparted taken while using Ubuntu (thus showing some partitions locked), but I am trying to repartition using a live CD.

Any help here would be appreciated.

---

### Post by cortman on 2012-04-23
First of all: BACK UP all your data that you can't afford to lose. Before you do anything else.

As far as adding the space, you can simply move all your partitions to the "left"- when you right click a partition in GParted, one of the options is "reszie/move". Select move, and define the new beginning and end point. Just shift the three partitions over until the unallocated space is next to the ext4 partition.
I've done this myself a couple times and had no problems at all. I understand it can be a tad risky depending on your HDD, so be sure your data is backed up first.

---

### Post by Cheesemill on 2012-04-23
Also bear in mind that it could take a while (as in plenty of hours, maybe even days) to move your current partitions.

Also cortman has the right idea about backups, I have lost a lot of data in the past when I have had a power cut during a gparted move operation.

If you have everything backed up then just go for it and then do the following:


[LIST]
[*]Extend your extended partition all the way to the left.
[*]Move sdb5 and sdb6 over to the left.
[*]Expand sdb7 to take up the free space in your extended partion.
[/LIST]

---

### Post by cortman on 2012-04-23
> **Cheesemill said:**
> Also bear in mind that it could take a while (as in plenty of hours, maybe even days) to move your current partitions.

+1 to this- if it seems like it's taking forever and not actually doing anything, pull out your Hitchhiker's Guide to the Galaxy and DON'T PANIC. :) Moving mine took about 4 hours.

---

### Post by forrestcupp on 2012-04-23
You also need to make sure that none of it is mounted, or it won't let you do it. If you're not already, you need to be running this from a LiveCD, and not your Ubuntu installation.

---

### Post by Cheesemill on 2012-04-23
> **forrestcupp said:**
> You also need to make sure that none of it is mounted, or it won't let you do it. If you're not already, you need to be running this from a LiveCD, and not your Ubuntu installation.
From the OP:
> but I am trying to repartition using a live CD

---

### Post by oldfred on 2012-04-23
Another choice.

Just make the unallocated anther partition. You have available sda3 as a primary partition or can just move the start of the extended left which should not take any time. I might suggest just making it a primary partition.

Then you can move /home into the new partition leaving lots of room in / (root).

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Cheesemill on 2012-04-23
> **oldfred said:**
> Another choice.

Just make the unallocated anther partition. You have available sda3 as a primary partition or can just move the start of the extended left which should not take any time. I might suggest just making it a primary partition.

Then you can move /home into the new partition leaving lots of room in / (root).

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

+1

Good spot oldfred.

Creating a separate /home partition is a lot let risk than moving your current setup. It will also let you keep all of your documents and settings intact if you ever need to reinstall or do a fresh install of Ubuntu.

---

### Post by dishbert on 2012-04-23
Thanks for the replies!

Everything is backed up.  When I booted to the live CD I did not see a way to extend the "Extended" partition, but I'll look again.

Perhaps my fear of deleting partitions is unwarranted?  I had a problem when the UUID's were changed and I ended up with a "File System check failed" message but that was 3 years ago, perhaps Ubuntu is smarter these days.  

I've backed up the contents of the 2 FAT32 partitions, would it be simpler to delete them?

---

### Post by forrestcupp on 2012-04-23
> **Cheesemill said:**
> From the OP:

You edited that in there, didn't you? :oops:

---

### Post by Cheesemill on 2012-04-23
> **forrestcupp said:**
> You edited that in there, didn't you? :oops:

Nope, just a straight forward quote :)

---

### Post by dishbert on 2012-04-23
I've been out to the Live CD again and the extended partition (sdb2) only has the options "Manage Flags" and "Information" available.  It shows as being locked even when viewed from the Live CD. It is flagged as lba.  Am I missing something here?

I like oldfred's suggestion about moving /home.  

I assume oldfred meant sdb3?  not sda3?

If I understand correctly the suggestion is that I make the unallocated space an EXT4 partition, which will then be named sdb3, and then follow the instructions in the link to move /home there.

This will take more time than I have at the moment, but I'll get at it later today or tomorrow and report back in this thread.

Thanks everyone!

---

### Post by oldfred on 2012-04-23
sdb3 is correct, oldfred must be getting old. :)

If still locked with liveCD it probably is swap. LiveCD's often use swap if found, so you have to unmount, but with swap is it not umount but swapoff. Click on swap and right click swap-off.

---

### Post by dishbert on 2012-04-23
Well I created sdb3 as an ext4 partition with no trouble, but following the guide to move /home something seems to have gone awry with the rsync command.  

As you can see, it seems to complete successfully, but the differences show that nothing in the /home/chris directory got copied.

chris@chris-linux-downstairs ~ $ sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/.
chris@chris-linux-downstairs ~ $ sudo diff -r /home /media/home
Only in /home/chris: .adobe
Only in /home/chris: .anomos
Only in /home/chris: .bash_history
Only in /home/chris: .bash_logout
Only in /home/chris: .bogofilter
Only in /home/chris: Bridge
Only in /home/chris: .cache

I stopped it at .cache.

chris@chris-linux-downstairs ~ $ ^C

chris@chris-linux-downstairs ~ $ cd /media/home
chris@chris-linux-downstairs /media/home $ ls
chris  lost+found  marilyn  remastersys
chris@chris-linux-downstairs /media/home $ cd chris
chris@chris-linux-downstairs /media/home/chris $ ls
chris@chris-linux-downstairs /media/home/chris $ 

Would the cp command work here instead?

---

### Post by oldfred on 2012-04-23
Many have used the rsync command. What is different?

You can use cp but must use the -a to be sure that ownership & permissions are copied.

Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dishbert on 2012-04-23
Hmmm........the cp -ax command copied everything except the "hidden" files over to /media/home/chris



chris@chris-linux-downstairs ~ $ cd ..
chris@chris-linux-downstairs /home $ ls
chris  marilyn  remastersys
chris@chris-linux-downstairs /home $ cd chris
chris@chris-linux-downstairs ~ $ sudo cp -ax * /media/home/chris
chris@chris-linux-downstairs ~ $ sudo diff -r /home /media/home
Only in /home/chris: .adobe
Only in /home/chris: .anomos
Only in /home/chris: .bash_history
Only in /home/chris: .bash_logout
Only in /home/chris: .bogofilter
Only in /home/chris: .cache
Only in /home/chris: .compiz
Only in /home/chris: .config
Only in /home/chris: .conkyrc
Only in /home/chris: .dbus
Only in /home/chris: .dmrc
Only in /home/chris: .dosbox
^C

I must be doing something wrong.  Maybe I should start all over?

To review:

This command copied everything in /home except the contents of /home/chris

sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/.

And this command copied the contents of /home/chris except the .* files

sudo cp -ax * /media/home/chris

Yikes!

---

### Post by oldfred on 2012-04-23
What format did you use for your new partition?

type this and post terminal output:

```
mount
```

It seems like permissions are not set correctly so it will not copy something.

---

### Post by dishbert on 2012-04-23
Thanks for sticking with me.  I used ext4 because that's what my existing Ubuntu system uses.

chris@chris-linux-downstairs /media/home/chris $ mount
/dev/sdb7 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb3 on /media/home type ext4 (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/chris/.Private on /home/chris type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_sig=218d024f01fc9d07,ecryptfs_fnek_sig=2a2ba3aba0143b55,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
/dev/sdd1 on /media/LEXAR type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sde1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/Iomega HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6 on /media/53E8-436A type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

---

### Post by oldfred on 2012-04-23
I have not dealt with encryption, so I wonder if that is part of the issue? You may need to adjust the from location to your private directory?

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

[SIZE=1]> 

After logging back in, all content of any files or folders you write in ~/Private will be encrypted when written to the disk, in the hidden directory ~/.Private.

[/SIZE]

---

### Post by dishbert on 2012-04-24
I had the thought to use a tar command to move the /home contents over to /media/home.  I had previously used one to back up my system (including the encrypted files) with no significant errors.

The backup command I'd used previously was:

chris@chris-linux-downstairs /media/Iomega HDD/Backups/Mint $ sudo tar cpzf mintbackup.tgz --exclude=/mintbackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media /

I'm not much of a tar expert, so the command I thought would just zip up the contents of my /home folder ended up zipping most of the root directory including /home!  Nevertheless, I only ended up with minor errors like:

many of these socket errors
tar: /home/chris/.anomos/ui_socket: socket ignored

many of these thumbnail errors
tar: /home/chris/.thumbnails/fail/gnome-thumbnail-factory/f459560db693ca2d949e276f233cf8f0.png.3C5ASV: Cannot open: Input/output error

and these 3 errors

tar: /home/chris/.evolution/mail/local/Outbox.ibex.index.data: Cannot open: Input/output error
tar: /home/chris/.evolution/mail/local/Outbox.ibex.index: Cannot open: Input/output error
tar: /home/.ecryptfs/chris/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWYe8uCfc.EvJEQFTtmq6.9n9sTyoMOV4AkyW5e6id1-b9wjXt74.H5cz---/ECRYPTFS_FNEK_ENCRYPTED.FWYe8uCfc.EvJEQFTtmq6.9n9sTyoMOV4AkyqheuhAw2cBTCx5QUsHHuiU--: socket ignored

So far so good!

Since I had no clue how to extract only the contents of the home directory from the tar file, I used sudo nautilus to do that, but it failed with an error.

If someone could tell me the correct command to zip up the /home contents and deposit the tar file in /media/home, and then the one to unzip them there, I might just get somewhere!

---

### Post by dishbert on 2012-04-24
OK, I guess I stared at it long enough to figure out the first command:

chris@chris-linux-downstairs /media/home $ sudo tar cpvzf home.tgz /home/

This worked and put the tarball in the right directory.

When I unpacked it though, there are no executables viewable in the /home/chris directory.  This is the encrypted directory, and maybe should be expected? 

But both the chris and marilyn directories are locked, which can't be right?  There is nothing encrypted in the marilyn directory.

chris@chris-linux-downstairs /media/home $ cd chris
bash: cd: chris: Permission denied

chris@chris-linux-downstairs /media/home $ cd marilyn
bash: cd: marilyn: Permission denied

The executables seem to be present in the marilyn folder.

---

### Post by oldfred on 2012-04-24
Still know nothing about encryption, but last link mentions mounting it separately as a regular folder first. Not sure about restore to encrypted then? Other discuss parameters.

HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
/home with tar - matthew
[http://ubuntuforums.org/showthread.php?t=1964130](http://ubuntuforums.org/showthread.php?t=1964130)
Mount encrypted first
[http://askubuntu.com/questions/58256/tar-backing-up-an-encrypted-home-folder](http://askubuntu.com/questions/58256/tar-backing-up-an-encrypted-home-folder)

---

### Post by dishbert on 2012-04-25
Thanks for all your suggestions oldfred.

I also found this thread which details no less than 3 methods to move an encrypted home folder to a new partition.

[http://askubuntu.com/questions/17332/how-can-i-move-an-encrypted-home-directory-to-another-partition](http://askubuntu.com/questions/17332/how-can-i-move-an-encrypted-home-directory-to-another-partition)

Alas, I have run out of time for this project as I'm headed off on a holiday today.  I will get back to it in a couple of weeks and report back to this thread.

Thanks again.

---

### Post by dishbert on 2012-04-29
Well my holiday got delayed a couple of days so I got back on this horse and finally had success.

I followed the link oldfred gave me up but kept missing a bunch of files in the /home/chris folder when I compared it to the original folder.  I found the link shown in my note above and tried it.

I did a
chown -hR chris /media/home

and 
ecryptfs-umount-private

and 
rsync -avP $HOME/.Private $HOME/.ecryptfs /new_mount_point/$USER

then used the rsync command to copy the home folder across, but I was still missing the executables in the /chris folder of the new mount point, so I did another rsync to just copy the contents of the /chris folder and that worked!

I did not have to use this instruction:
editor /etc/passwd # Change the user's home dir to point to the new location

This time the comparison showed a bunch of not very important files still missing, but I took a chance and modified the fstab file and rebooted and it all worked fine!

The problem must have been the encryption of the /home/chris folder, which was nothing unusual, just ticking that box when I installed Ubuntu.

Thanks everyone, especially oldfred.  I now have room to breath for my home folder.

---

### Post by oldfred on 2012-04-29
Glad you were able to figure it out. 

I have not dealt with encryption and have avoided it because of the extra complications. But if you need security on a portable or example then it may be worth having.

---

