---
title: "Think I May Have Had A Brain Fart"
date: 2009-12-23
forum: General Help
---

### Post by 5BallJuggler on 2009-12-23
Once upon a time, this guy was using Ubuntu, and reading these forums, he was looking at trying to make his system better.
He decided it would be a good idea to seperate his /home folder onto a new partition.
He read through the info that the many kind users had voluntarily placed in these hallowed pages and thought it sounded straight forward.
He made a new partition.
He copied all of his /home folder onto the new partition.(after a nightmare trying to get it to mount) he used the mountmanager package to set up his new partition
This package said" is it OK to alter your fstab file.
"yes" the guy said, knowing that all would be well.
Thinking that this was the end of the process the guy thought I will now boot up and check the system, if it's OK i will delete my old /home file and all will be well.
When the computer started it failed at the mountall command.
"S**T!" said the guy
I know, i'll boot up with the USB that I have created
on doing this the 150Gb harddrive in the netbook would not mount
"I'll remove the new partition" he thought.
this made a bigger partition that still wouldn't mount.
after much rebooting and playing with the mount options in the terminal and disk utility functions the drive mounted and the fstab file was checked
```
UUID=603ab879-f6f6-4aa3-8624-a692fcc5ad11 / ext3 users 0 0
```
was all he saw, "mmmm?" thought the guy.
"that was the UUID of the new partition, where is the original one?"
"No wonder it would not work!"
he then replaced the fstab with fstab.bak
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a30df058-2406-4a48-9445-e80fb22db47a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e9d62386-afa3-4d14-9c78-da1444d840a8 none            swap    sw              0       0
```
.....And all was well!
.....And all was exactly how it was to begin with.

Can you please help the guy find out where he went wrong.

Thanks in Advance
Phil

ps The guy was me! :oops:

---

### Post by nothingspecial on 2009-12-23
Do it all again and when you have copied your home, put an entry in fstab like this```


UUID=4402fbf3-734c-4238-9b56-635ddc422741 /home           ext3 defaults        0       2
```

You will then have to change the owner of it and everything in it to you and change the permissions on a couple of things.

You find the uids of partitions by typing ```
sudo blkid
``` just change the one I posted to your new one.

---

### Post by 5BallJuggler on 2009-12-23
OK, system wont boot up, this is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a30df058-2406-4a48-9445-e80fb22db47a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=fb708689-029a-4f8e-bb17-09d672ea161a /home 	  ext3 	  defaults        0       2
# /dev/sda5
UUID=e9d62386-afa3-4d14-9c78-da1444d840a8 none            swap    sw              0       0
```

This is my sudo blkid while running from liveUSB

```
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="830f4f8c-c9d2-46d4-b67f-f28aed9df8d6" TYPE="ext3" 
/dev/sda1: UUID="a30df058-2406-4a48-9445-e80fb22db47a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="fb708689-029a-4f8e-bb17-09d672ea161a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e9d62386-afa3-4d14-9c78-da1444d840a8" TYPE="swap" 
/dev/sdb1: LABEL="" UUID="6C0B-E1A8" TYPE="vfat" 

```

This is my cat /media/sda1/etc/mtab

```

ubuntu@ubuntu:~$ cat /media/sda1/etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0

```

Any ideas where i'm going wrong?

Phil

---

### Post by ricardo.gloe on 2009-12-23
What guide(s) did you use to (try to) create a separate home partition? From what you've said, the only thing I can think of are permission problems. How did you copy your original home to the new home partition?

---

### Post by 5BallJuggler on 2009-12-23
> **ricardo.gloe said:**
> What guide(s) did you use to (try to) create a separate home partition? From what you've said, the only thing I can think of are permission problems. How did you copy your original home to the new home partition?

I did not follow one particular guide, but an amalgamation of quite a few that don't seem to work, I picked the most simplistic method I could find
I used nautilus from the liveUSB to move the folder.

incidently if i create a new fstab file on the liveUSB, it mounts sda1/ OK, but it says that sda3/home is not an available mount point.

Phil

---

### Post by john newbuntu on 2009-12-23
Did you unmount the old home, move the (old) /home out of the way and remount the new home after changing fstab and before rebooting?   Note that when the system boots up it should see only one /home and that in your case should be the new one.  Also check /var/log/kern.log and /var/log/messages for any errors at boot/mount time.  

Here's another guide for you.  Follow these exactly: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by 5BallJuggler on 2009-12-23
> **john newbuntu said:**
> Did you unmount the old home, move the (old) /home out of the way and remount the new home after changing fstab and before rebooting?   Note that when the system boots up it should see only one /home and that in your case should be the new one.  Also check /var/log/kern.log and /var/log/messages for any errors at boot/mount time.  

Here's another guide for you.  Follow these exactly: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

I'm gonna have a play with this tomorrow, do i need to set permissions in the new partition? if so, how?

Phil

---

### Post by john newbuntu on 2009-12-24
Not if you have copied using the rsync command as root.

---

### Post by nothingspecial on 2009-12-24
> **5BallJuggler said:**
> I'm gonna have a play with this tomorrow, do i need to set permissions in the new partition? if so, how?

Phil

From root shell```


chown -R phil:phil /home/phil/

chmod 644 /home/username/.dmrc

chmod 644 /home/username/.ICEauthority
```

---

### Post by ricardo.gloe on 2009-12-24
I've successfully moved /home using this command:

```
$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```

Picked it up from [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)


but a rsync or cp -a should work also.

---

### Post by 5BallJuggler on 2009-12-24
> **john newbuntu said:**
> Did you unmount the old home, move the (old) /home out of the way and remount the new home after changing fstab and before rebooting?   Note that when the system boots up it should see only one /home and that in your case should be the new one.  Also check /var/log/kern.log and /var/log/messages for any errors at boot/mount time.  

Here's another guide for you.  Follow these exactly: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Many thanks for the help,  tried this this morning and it worked flawlessy (apart from the "umount /mnt/home" it says it was already running and couldn't be unmounted, left it 10 minutes and tried again, still NG, decided to do the next step anyway. It worked)

so once again thanks for your help.
Have a merry chrimbo

Phil

---

