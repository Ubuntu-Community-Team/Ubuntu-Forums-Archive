---
title: "fstab refuses to mount drive corectly 12.04"
date: 2012-05-21
forum: General Help
---

### Post by MadBillyGoat on 2012-05-21
OK I have been trying to do this for EVER....
This started several versions back.
I am unable to edit fstab correctly.
I have done it with NP up until ubuntu 11....
I am done.

I will edit fstab as root.
I will then reload fstab.

     It will reload fstab and the mounted drive will appear where specified. In /home/madbillygoat/media.
As It is to.
NOW!

When I reboot the drive does not appear in the correct dir. It appears to be noware but nautilus side bar indicates that it is mounted.. And nothing can unmount or mount it.   The "Mounted drive" is nowhere to be found on the system or accessed.  but I can see graphically that it thinks it is mounted..

I have used all ways I can think of to fix this the last couple are:

#Windows-Partition
UUID=7BD0074C7A112B0A /home/madbillygoat/Music ntfs rw,auto,users,exec,nls=utf8,umask=003,gid=46,uid=1000    0   2

UUID=7BD0074C7A112B0A     /home/madbillygoat/Music       ntfs    defaults    0    0

/dev/sdb1 /home/madbillygoat/Music       ntfs    defaults    0    0

Thare are many other ver. but I cant remember them..
I am sick of looking for the answer.
The same result aways happens.. It is there and working before reboot.

Something has been changed the last couple years and I don't know.

Thanks.

---

### Post by MadBillyGoat on 2012-05-21
Also I had no problem doing this in Debian.  Just last week.
I think it has something to do with the new gnome or unity.. horrible things they are..
I am using gnome-panel  seems to be ok at best Miss the old v2.

---

### Post by wilee-nilee on 2012-05-21
Post the output of both of these to get help.

```
sudo blkid
``````
sudo gedit /etc/fstab
```If you notice the second command is a read write, that is your superuser/root access.

---

### Post by raja.genupula on 2012-05-21
+1 to above post , but the simple way we have is 

```
cat /etc/fstab
``` no need to go for sudo in this . :) :) 


cheers !

RAJA

---

### Post by bodhi.zazen on 2012-05-21
Should be ntfs-3g and I would advise the permissions option

UUID=7BD0074C7A112B0A /home/madbillygoat/Music ntfs-3g permissions 0 0

List your partition only once and make sure the UUID is correct.

Then make sure ~/Music exists

---

### Post by wilee-nilee on 2012-05-21
> **raja.genupula said:**
> +1 to above post , but the simple way we have is 

```
cat /etc/fstab
``` no need to go for sudo in this . :) :) 


cheers !

RAJA

The user mentioned debian and having to go root, debian can use sudo many do not set it up that way.

If you look closer this was a example of how to edit it in Ubuntu.

---

### Post by raja.genupula on 2012-05-22
Yeah i agree with you but i read your first line of that post as output , so i have given as like that . beause to get output cat is enough :) .

---

### Post by MadBillyGoat on 2012-05-22
Hello again.
Thank you for he help guys.. 
I know how to edit  the file how to get there and everything.. 
 I have been modifying my fstab and geting my drives to mount in my home directory with no problem ever sense I started using ubuntu 9.06 I think 06  been a while.

The issue is that the format I used before is no longer working and I have tried many different ways of doing it..
I need Examples of peoples fstab.  
SO 
If anyone has modified there fstab to mound an ntfs file system into here home directory I would like the exact line posted.. I can changed it to work in my system.

This is my orginal format that worked for years.. Of cours the uuids and directories have changed over the years but this is the format:

UUID=5878EA177587DF2A    /home/office2/Office        ntfs    defaults    0    0

This is the last one I tried with a nogo:

UUID=2875A6F278A77F5Z /media/DATA ntfs-3g defaults 0 0

Even the ones listed in the first post have had the same result.


Now with both of these formats before I reboot the system I reload the fstab... aka "sudo mount -a"
and the drive mounts and appears in the home dir.  and functions correctly.

I then reboot and the drive is nowhere to be found..  And I am unable to use view unmount mount the drive.. Even though It shows being mounted in nautilus.
See Very frustrating.
I don't know if i need a lib or something to make this all work.. I have researched all over and have not found an answer...  This is my last hope...  

Thanks for the help guys.. Keep it coming.. ):P

---

### Post by MadBillyGoat on 2012-05-22
> **bodhi.zazen said:**
> Should be ntfs-3g and I would advise the permissions option

UUID=7BD0074C7A112B0A /home/madbillygoat/Music ntfs-3g permissions 0 0

List your partition only once and make sure the UUID is correct.

Then make sure ~/Music exists

Ok I did this.
Same issue
Reloaded fstab and IT showed in the home dir. as expected.
Except
This time I could not write to the dir.  I coud read and copy  but no writing...
I then rebooted and the same thing happen it was gone.. when I click the mounted drive in nautilus all i get is the Directory in my home folder. Not the "mounted drive"
Thanks for the attempt.. 
Have any more. Ill keep trying anything ya got..  
Thanks again.  :p

---

### Post by Morbius1 on 2012-05-22
The ntfs filetype in Ubuntu points to the ntfs-3g driver and there is no such option as "permissions" assuming you took that literally. But let's go back to this from your original post:
>  UUID=7BD0074C7A112B0A     /home/madbillygoat/Music       ntfs    defaults    0    0There is absolutely no reason why that would not work.

I'm afraid you are going to have to post a lot of info if you want to resolve this once and for all so please post the output of the following commands:
```
cat /etc/fstab
``````
sudo blkid -c /dev/null
``````
mount
```

---

### Post by bodhi.zazen on 2012-05-22
> **Morbius1 said:**
> The ntfs filetype in Ubuntu points to the ntfs-3g driver and there is no such option as "permissions" assuming you took that literally.


That is not true, read the man page

[http://linux.die.net/man/8/mount.ntfs-3g](http://linux.die.net/man/8/mount.ntfs-3g)

> permissions
    Set standard permissions on created files and use standard access control. This option is set by default when a user mapping file is present. 

At any rate, once it is mounted, you can then chown and chmod the ntfs system 

```
sudo chown -R your_user:your_user /home/madbillygoat/Music 
```

should be sufficient. You can chmod if needed.

---

### Post by Morbius1 on 2012-05-22
I don't know where to start with that post. But I guess I'll focus on this statement instead of dragging this though a 15 post ego driven rat hole to see who's tech-foo is stronger:

> At any rate, once it is mounted, you can then chown and chmod the ntfs system 

     Code:
     ```
sudo chown -R your_user:your_user /home/madbillygoat/Music
```You cannot - I repeat - you cannot chmod or even chown an NTFS partition. NTFS partitions are mounted with a "view" where the ownership and permissions are defined by the mount and are immutable. And in case you are wondering if you chmod or chown the mount point before the partition is mounted it won't work either. A mounted partition always overrides the permissions of the mount point.

---

### Post by bodhi.zazen on 2012-05-22
> **Morbius1 said:**
> I don't know where to start with that post. But I guess I'll focus on this statement instead of dragging this though a 15 post ego driven rat hole to see who's tech-foo is stronger:

You cannot - I repeat - you cannot chmod or even chown an NTFS partition. NTFS partitions are mounted with a "view" where the ownership and permissions are defined by the mount and are immutable. And in case you are wondering if you chmod or chown the mount point before the partition is mounted it won't work either. A mounted partition always overrides the permissions of the mount point.

You really should read the man page and try these things

[http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner](http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner)

```
bodhi@ufbt:/media$ touch ntfs/test_file
bodhi@ufbt:/media$ ls -la ntfs/   

**[COLOR="SeaGreen"]-rw-r--r-- 1 bodhi bodhi[/COLOR]**    0 2012-05-22 07:16 test_file

bodhi@ufbt:/media$ sudo chown root:bodhi ntfs/test_file

bodhi@ufbt:/media$ ls -la ntfs

-rw-r--r-- 1 [COLOR="DarkRed"]root  bodhi[/COLOR]    0 2012-05-22 07:16 test_file
```

Permissions persist if you umount and remount the ntfs partition.

fstab entry
```
/dev/sda5 /media/ntfs ntfs-3g exec,permissions 0 0
```

---

### Post by Morbius1 on 2012-05-22
When you find yourself in a hole the first thing you should do is stop digging:
> OK, I got everything working on the Ubuntu side, with the following options:
  nls=iso8859-1,permissions,users,auto,exec
  However, when I try to access files on the partition from Windows,  the security settings are all messed up. On all the files (of those few  I've examined) a new account called Account Unknown(long GUID)  has been added to the list of users, and has full rights. Rigths for  most other users are decreased so that I don't have rights to do stuff I  expect. Notably "Everyone" does no longer seem to have right to  "Traverse folder / execute".
  This might be solvable by just selecting the partition and  allow Everyone to do anything on the root folder, and then tell it to do  it recursively, but I'd rather not as I'm afraid it will take days to  complete...


---

### Post by bodhi.zazen on 2012-05-22
> **Morbius1 said:**
> When you find yourself in a hole the first thing you should do is stop digging:

Or read the man page / documentation.

[http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)

[http://b.andre.pagesperso-orange.fr/usermap.html](http://b.andre.pagesperso-orange.fr/usermap.html)

Using your logic, one would quit using computers the first bug / problem they encounter.

As with all things, more complex mounts require more complex configuration.

---

### Post by MadBillyGoat on 2012-05-22
Hello and thanks guys I hope this info helps.

output:
madbillygoat@GoatLand:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=c1294546-098a-4d9e-a627-6725c19f3806 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=befc53a3-a2aa-4a1a-a38e-2286e0eafa15 /boot           ext4    defaults        0       2
# /home was on /dev/sdc9 during installation
UUID=81206b6f-d945-4eec-bbf0-5b0c4c6c89af /home           ext4    defaults        0       2
# /tmp was on /dev/sdc7 during installation
UUID=7bce2899-193b-4b80-92a3-f502d9500cea /tmp            ext4    defaults        0       2
# /usr was on /dev/sdc8 during installation
UUID=c1596c93-dd26-4f35-8126-ec838f453db4 /usr            ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
#UUID=9d225ebe-bb96-4689-bf69-25d34185c640 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

# Windows Media Drive /dev/sbd2:
UUID=7BD0074C7A112B0A /home/madbillygoat/Music ntfs defaults 0 0 


This includes the line I added which works when I reload fstab but not on reboot.


madbillygoat@GoatLand:~$ sudo blkid -c /dev/null
[sudo] password for madbillygoat: 
/dev/sda1: LABEL="System Reserved" UUID="883845013844EFAC" TYPE="ntfs" 
/dev/sda2: LABEL="System" UUID="96C24E84C24E6917" TYPE="ntfs" 
/dev/sdb1: LABEL="DVD" UUID="6F75AA6E21DE9607" TYPE="ntfs" 
/dev/sdb2: LABEL="Media" UUID="7BD0074C7A112B0A" TYPE="ntfs" 
/dev/sdc1: UUID="befc53a3-a2aa-4a1a-a38e-2286e0eafa15" TYPE="ext4" 
/dev/sdc6: UUID="c1294546-098a-4d9e-a627-6725c19f3806" TYPE="ext4" 
/dev/sdc7: UUID="7bce2899-193b-4b80-92a3-f502d9500cea" TYPE="ext4" 
/dev/sdc8: UUID="c1596c93-dd26-4f35-8126-ec838f453db4" TYPE="ext4" 
/dev/sdc9: UUID="81206b6f-d945-4eec-bbf0-5b0c4c6c89af" TYPE="ext4" 
/dev/sdd1: LABEL="2TB_Backup" UUID="56D8E1FFD8E1DCED" TYPE="ntfs" 
/dev/mapper/cryptswap1: UUID="79d7482b-aada-400a-bfa3-83d8ab19731e" TYPE="swap" 


madbillygoat@GoatLand:~$ mount
/dev/sdc6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /boot type ext4 (rw)
/dev/sdc7 on /tmp type ext4 (rw)
/dev/sdc8 on /usr type ext4 (rw)
/dev/sdc9 on /home type ext4 (rw)
/dev/sdb2 on /home/madbillygoat/Music type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/madbillygoat/.Private on /home/madbillygoat type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=f0ffb3db815aaf1b,ecryptfs_fnek_sig=cbec29b3f8153fb1)
gvfs-fuse-daemon on /home/madbillygoat/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=madbillygoat)
/dev/sdd1 on /media/2TB_Backup type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

OK guys here is all the codes entered and there outputs..

This is also the error when I try to unmount the easy way in Nautilus...

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=7BD0074C7A112B0A from /home/madbillygoat/Music


I hope someone can add some light to this...  I simply don't know anymore..

---

### Post by bodhi.zazen on 2012-05-22
> **MadBillyGoat said:**
> Hello and thanks guys I hope this info helps.

output:
madbillygoat@GoatLand:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=c1294546-098a-4d9e-a627-6725c19f3806 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=befc53a3-a2aa-4a1a-a38e-2286e0eafa15 /boot           ext4    defaults        0       2
# /home was on /dev/sdc9 during installation
UUID=81206b6f-d945-4eec-bbf0-5b0c4c6c89af /home           ext4    defaults        0       2
# /tmp was on /dev/sdc7 during installation
UUID=7bce2899-193b-4b80-92a3-f502d9500cea /tmp            ext4    defaults        0       2
# /usr was on /dev/sdc8 during installation
UUID=c1596c93-dd26-4f35-8126-ec838f453db4 /usr            ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
#UUID=9d225ebe-bb96-4689-bf69-25d34185c640 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

# Windows Media Drive /dev/sbd2:
UUID=7BD0074C7A112B0A /home/madbillygoat/Music ntfs defaults 0 0 


This includes the line I added which works when I reload fstab but not on reboot.


madbillygoat@GoatLand:~$ sudo blkid -c /dev/null
[sudo] password for madbillygoat: 
/dev/sda1: LABEL="System Reserved" UUID="883845013844EFAC" TYPE="ntfs" 
/dev/sda2: LABEL="System" UUID="96C24E84C24E6917" TYPE="ntfs" 
/dev/sdb1: LABEL="DVD" UUID="6F75AA6E21DE9607" TYPE="ntfs" 
/dev/sdb2: LABEL="Media" UUID="7BD0074C7A112B0A" TYPE="ntfs" 
/dev/sdc1: UUID="befc53a3-a2aa-4a1a-a38e-2286e0eafa15" TYPE="ext4" 
/dev/sdc6: UUID="c1294546-098a-4d9e-a627-6725c19f3806" TYPE="ext4" 
/dev/sdc7: UUID="7bce2899-193b-4b80-92a3-f502d9500cea" TYPE="ext4" 
/dev/sdc8: UUID="c1596c93-dd26-4f35-8126-ec838f453db4" TYPE="ext4" 
/dev/sdc9: UUID="81206b6f-d945-4eec-bbf0-5b0c4c6c89af" TYPE="ext4" 
/dev/sdd1: LABEL="2TB_Backup" UUID="56D8E1FFD8E1DCED" TYPE="ntfs" 
/dev/mapper/cryptswap1: UUID="79d7482b-aada-400a-bfa3-83d8ab19731e" TYPE="swap" 


madbillygoat@GoatLand:~$ mount
/dev/sdc6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /boot type ext4 (rw)
/dev/sdc7 on /tmp type ext4 (rw)
/dev/sdc8 on /usr type ext4 (rw)
/dev/sdc9 on /home type ext4 (rw)
/dev/sdb2 on /home/madbillygoat/Music type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/madbillygoat/.Private on /home/madbillygoat type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=f0ffb3db815aaf1b,ecryptfs_fnek_sig=cbec29b3f8153fb1)
gvfs-fuse-daemon on /home/madbillygoat/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=madbillygoat)
/dev/sdd1 on /media/2TB_Backup type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

OK guys here is all the codes entered and there outputs..

This is also the error when I try to unmount the easy way in Nautilus...

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=7BD0074C7A112B0A from /home/madbillygoat/Music


I hope someone can add some light to this...  I simply don't know anymore..

Only root can mount / umount ntfs

sudo umount ....

Also your other problem is you are using an encrypted home directory. So the partition can not mount at boot as your home directory is encrypted. Either mount it outside of home and use links or do not use an encrypted home or mount it manually.

---

### Post by MadBillyGoat on 2012-05-22
HA...!!!  The encrypted Directory.. That is it.. It Must be...  It is the only other thing I started doing differently sense Ubuntu 11....

How the Heck do I turn that thing off or disable or what can I do.. It is set up during instillation.. 
That makes perfect sense...  I should have thought of it..  Don't you love the Light bulb...:P
Well how to do remove the encryption?

Thanks huge guys..

---

### Post by MadBillyGoat on 2012-05-22
You get a error when you goto mount unmount the drive in terminal..
Thanks

---

### Post by MadBillyGoat on 2012-05-22
Is there a way to script the encryption code into the fstab or a script that will mount it in the home folder during start up?

---

### Post by MadBillyGoat on 2012-05-22
OK I made a launcher with this line
"gksudo  mount    /dev/sdb2   /home/madbillygoat/Music/"
It launches in start up and all I have to do is enter my password.
But for some reason I am unable to type.. I have to unplug and replug my keyboard for the keyboard to work.. It is a logitech unity thing..
So Is there a way to make this little launcher launch last in the startup?
Also
If anyone has any answers to my questions above.. That would be great..

Thanks

---

### Post by bodhi.zazen on 2012-05-23
The easiest thing to do, by far, is mount your ntfs partition in /media

You can then link it to ~/Music

```
ln -s /media/Music ~/Music
```

---

