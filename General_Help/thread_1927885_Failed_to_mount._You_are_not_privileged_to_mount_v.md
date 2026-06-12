---
title: "Failed to mount. You are not privileged to mount volume"
date: 2012-02-18
forum: General Help
---

### Post by fleamour on 2012-02-18
I am running Xubuntu 10.04 LTS & use a hot swap secondary HDD to save backup images.  It was formatted to NTFS since I historically used to dual boot with Win2k, & this has always worked fine.  However it never sees a Windows machine any more, so thought at least it'll get a disk check every now & then when formatted to ext4.  I formatted to ext4 with Parted Magic & that is where the problems started.  

I tried deleting a backup but I did not have sufficient read/write privileges.  I could not change read/write access via right click properties context menu.  I formatted drive again from CLI within Xubuntu hoping it might help.  Every time I connect the volume I get 'Failed to mount "SKYDRIVE".  You are not privileged to mount "SKYDRIVE".'

Google did not yield a definitive answer.

So...anyone?

I would like it to auto mount like it did before with NTFS.

:confused: :-( :confused:

---

### Post by ankspo71 on 2012-02-19
Hi,
Are you mounting the ntfs partition with /etc/fstab? If you are please open a terminal and paste in the following so you can post the output of:
```
cat /etc/fstab
```
It might only be a matter of an incorrect mount option (or maybe a typo) since reformatting your drive. The device name and or UUID might not be correct too.

> I tried deleting a backup but I did not have sufficient read/write privileges. I could not change read/write access via right click properties context menu


Newly created partions (and the files within them) that are not mounted in your home folder are going to be automatically owned by root, so you will need to use sudo to be able to have full read and write access. 
Hope this helps.

---

### Post by fleamour on 2012-02-19
The partition was NTFS, it is now ext4.  I use a caddy that swaps out in place of laptop DVD drive.
```
fleamour@IBM-T21:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=019d6fe4-f134-4fa0-ba35-61957d3e359c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=a4141151-2467-47ac-ae6c-25cbb1cfb97c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=128c25a0-148e-42b4-afcd-16899bccc7bb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

It appears not to be listed.  Do I have to manually mount with sudo each time?  I have not done this before.

---

### Post by fleamour on 2012-02-19
Wiki:  "The fstab file typically lists all available disks and disk partitions, and indicates how they are to be initialized or otherwise integrated into the overall system's file system... It is the duty of the system administrator to properly create and maintain this file."
```
fleamour@IBM-T21:~$ blkid
/dev/sdb1: LABEL="SKYDRIVE" UUID="73b78481-6005-4e2f-94fe-bc1775a469a8" TYPE="ext4" 
/dev/sda2: UUID="019d6fe4-f134-4fa0-ba35-61957d3e359c" TYPE="ext4" 
/dev/sda3: UUID="a4141151-2467-47ac-ae6c-25cbb1cfb97c" TYPE="ext4" 
/dev/sda5: UUID="f04f0dab-7f8b-435a-8e43-855da7b3ac42" TYPE="swap"
```

How would I integrate this info into fstab?

---

### Post by TheFu on 2012-02-19
Pick a stanza from your existing /etc/fstab and copy it for the new HDD.  Edit the copied line for the new partition to be mounted.  Be certain to change the UUID, file system type **and** mount point or it will probably turn out badly.  If the new HDD isn't always available, you'll want to change some options.

[http://manpages.ubuntu.com/manpages/dapper/man5/nfs.5.html](http://manpages.ubuntu.com/manpages/dapper/man5/nfs.5.html) explains all the options in the /etc/fstab file.

After you are happy with the file, tell the system to mount it:
$ sudo mount -a

---

### Post by fleamour on 2012-02-19
> **TheFu said:**
> Pick a stanza from your existing /etc/fstab and copy it for the new HDD.  Edit the copied line for the new partition to be mounted.  Be certain to change the UUID, file system type **and** mount point or it will probably turn out badly.  If the new HDD isn't always available, you'll want to change some options.

[http://manpages.ubuntu.com/manpages/dapper/man5/nfs.5.html](http://manpages.ubuntu.com/manpages/dapper/man5/nfs.5.html) explains all the options in the /etc/fstab file.

After you are happy with the file, tell the system to mount it:
$ sudo mount -a

OK.  I understand.  Could you check below?

```
# /***<==This is root, what do I change it to? (/media/SKYDRIVE?)*** was on /dev/sdb1 during installation
UUID=73b78481-6005-4e2f-94fe-bc1775a469a8 /               ext4 ***<Any other options after this?>***
```

---

### Post by ankspo71 on 2012-02-19
Hi,
First, create a new mountpoint for SKYDRIVE. A mountpoint is only a regular folder, but it serves as a location to mount the partition.

```
sudo mkdir /media/SKYDRIVE
```

Now open fstab your text editor using root privleges:
```
gksudo leafpad /etc/fstab
OR
sudo nano /etc/fstab
```

Now you can add this line to fstab:
```
UUID=73b78481-6005-4e2f-94fe-bc1775a469a8 /media/SKYDRIVE ext4 users 0 0 
```
Then save the file. If you used nano to edit the file then press Ctrl+o to save the file, then press Ctrl+x to exit.

In the basic example I gave you, the mount option called "users" implies using the default mount options, except that it will allow the partition to be mounted automatically for any user. Note that this will not change the ownership of the files as they will still be owned by root. For a description of what each column in fstab means you can refer to this chart here: [https://help.ubuntu.com/community/Fstab#Fstab_File_Configuration](https://help.ubuntu.com/community/Fstab#Fstab_File_Configuration) If you would like to have full ownership (full read and write access for the user fleamore) of the files on the drive, you can issue a command like this:
```
sudo chown -R fleamour:fleamour /media/SKYDRIVE
```
Be sure to replace fleamour with your actual username.
Hope this helps.

---

### Post by fleamour on 2012-02-19
Same error, even after reboot.  I get:
```
fleamour@IBM-T21:~$ sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab

```

---

### Post by fleamour on 2012-02-19
OK, followed directions to the t & then left one "new line" at end of fstab, but ejecting/reinserting hot swapable HDD still brings up original error:  'Failed to mount "SKYDRIVE". You are not privileged to mount "SKYDRIVE".'

:(

---

### Post by fleamour on 2012-02-19
OK, read the man & settled for:

```
UUID=73b78481-6005-4e2f-94fe-bc1775a469a8 /media/SKYDRIVE ext4 rw,auto,user 0       2
```

Not seeing a typo

```
$ sudo mount -a
``` returns no errors so assume Fstab good.  But ejecting & reinserting hot swapable HDD still brings up original error: 'Failed to mount "SKYDRIVE". You are not privileged to mount "SKYDRIVE".'

I cannot copy & paste files to drive either.  Most strange, anyone have experience with this?  I am thinking of reverting to NTFS as this seemed to work automatically.  Maybe ext4 does not like hot swapping?

---

### Post by zergling on 2012-02-19
> **fleamour said:**
> OK, read the man & settled for:

```
UUID=73b78481-6005-4e2f-94fe-bc1775a469a8 /media/SKYDRIVE ext4 rw,auto,user 0       2
```

Not seeing a typo

```
$ sudo mount -a
``` returns no errors so assume Fstab good.  But ejecting & reinserting hot swapable HDD still brings up original error: 'Failed to mount "SKYDRIVE". You are not privileged to mount "SKYDRIVE".'

I cannot copy & paste files to drive either.  Most strange, anyone have experience with this?  I am thinking of reverting to NTFS as this seemed to work automatically.  Maybe ext4 does not like hot swapping?


This is normal because you have to set up the permissions
Open up a terminal and type 
```
sudo chmod 777 /media/SKYDRIVE -R
```

After this, you should be able to write on your HD.

Bye and let me know :)

---

### Post by fleamour on 2012-02-19
No, sorry, same error.

---

### Post by fleamour on 2012-02-19
I notice laptop will now not boot without secondary HDD present.  Is this because of the auto option in Fstab?

---

### Post by TheFu on 2012-02-20
Whoa!!!! 777?   That is a really bad idea.  'chown -R me.me *'  is a better idea, assuming your cwd is in the mounted area already.  If you don't understand this, please say something **before** you run the command.

Please learn about users, groups and file permissions. This is all that is happening - a file permissions issue. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The mount point directory needs to be owned by the uid:groupid you desire **before** a mount is attempted.  The mount point directory usually should be owned by root.  Create a subdir under it post-mount and make the owner/group whoever you like and make the permissions what you need.

After you understand users, groups and file permissions, this will seem simple.  Using this command
$ ls -alF
will provide lots of information if you have questions.

---

### Post by ankspo71 on 2012-02-20
> I notice laptop will now not boot without secondary HDD present. Is this because of the auto option in Fstab?
You (now obvious to me) still want to be able to hot plug the drive, so I apologize for the confusion and your wasted time. Anything listed in fstab is meant to be mounted at boot time. If a device is removed prior to starting the system, whether or not is was told to mount automatically, can cause the system to not start. The changes that were made in /etc/fstab can easily be removed to get back to where you were originally though.

So the question still remains, why won't the drive automatically mount once plugged in?...

Are you still using your administrator account (for example the original user account) when you log into *ubuntu? Do you still have permissions to 'Access external storage devices automatically'? Here is some info about mounting external drives: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

You should be able to rescue your backup files if you boot into your live cd then plug in your external drive.

---

### Post by fleamour on 2012-02-20
@ankspo71

OK thanks, that is interesting reading & I've learned something 'bout Fstab along the way, so no worries.  I think it must be a bug, all the proper options are ticked.  I will reformat to NTFS I think.  Bug may be fixed in Precise.  

@TheFu

> Whoa!!!! 777? That is a really bad idea. 'chown -R me.me *' is a better idea, assuming your cwd is in the mounted area already. If you don't understand this, please say something **before** you run the command.

I ran command in good faith.  Did Google to check not malicious, can I undo any damage?  I am going to reformat hot plug drive to NTFS so this may not matter?

Anyway, thanks everyone for there time & effort.

Cheerz

fleamour

---

### Post by fleamour on 2012-02-20
Hi

So it would appear to be a simple file permissions issue.  I have read up on it as stated:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

But theoretically:

```
sudo chmod 777 /media/SKYDRIVE -R
```

Should work, no?  (No matter the security risks.)

It doesn't, same permissions error.  Why the hot plug drive formerly worked as NTFS is beyond me, but neither file system works now.  

Can someone explain why?  The syntax seems correct to me.

---

### Post by TheFu on 2012-02-20
> **fleamour said:**
> 
```
sudo chmod 777 /media/SKYDRIVE -R
```Should work, no?  (No matter the security risks.)


a) Usually that command would be written:
```
sudo chmod -R 755  /media/SKYDRIVE 
```I changed the permissions to something "better" as an example.  However, that will not change the permissions for the mount point if the partition is already mounted.

If this doesn't result with something you are happy about, it is because your mount point doesn't have the correct ownership **before** you mount it.  Creating a subdir with the desired owner is usually easiest until you completely understand mount point ownership.

```
sudo mkdir  /media/SKYDRIVE/data
sudo chown you.you /media/SKYDRIVE/data

```Then you just put all your data inside   /media/SKYDRIVE/data.  

Actually, do you know that you don't need to mount under /media, right?  You can make any directory at any level and mount there. This isn't MS-Windows with drive letters after all.  /data or /home/you/data might be reasonable choices?

All my machines have a /backups mount point.  That's where I either mount a different HDD/partition for backups or where I mount via NFS a networked backup drive.

Anyway, just a few more thoughts for your consideration. I'm certain you will do what is best for your needs.

---

### Post by fleamour on 2012-02-20
Well I now have R/W access to SKYDRIVE.  I must admit I'm not entirely sure how, either:

```
chmod 777 <directory>
```

or

```
chown -R fleamour.fleamour <directory>
```

[http://serverfault.com/questions/39288/how-to-change-owner-of-mount-point](http://serverfault.com/questions/39288/how-to-change-owner-of-mount-point)

If anyone knows how to get rid of annoying 'Failed to mount "SKYDRIVE".' (It does mount.) 'You are not privileged to mount "SKYDRIVE".' pop up error, be my guest...

---

### Post by TheFu on 2012-02-21
Do you understand what '777' means?  If you are the owner of the file or directory, then only 700 is needed.
7 - owner - the userid
7 - group - members of the group, under ubuntu, that is usually the same as the userid.
7 - other - everyone else on the machine
This is like saying that everyone on the box can write there.  File permissions are critical to Linux security. This is much more important that users have been taught by Microsoft. Permissions work the same for local and remote users, unlike under MS-Windows.  THIS STUFF IS IMPORTANT. 777 is a major security issue on a UNIX system.  System admins around the world search out files and directories with 777 permissions and lock them down.

Please do not leave any files or directories with loose permissions.  Only /tmp should have sometime like these permissions and /tmp has the +t set to protect those files/directories.

I think you need to disable automatic mounting by whatever file manager you use.  It might be a service too.  I dunno, sorry. The downside for that is that connecting USB devices won't mount automatically.

We probably should have just sent you to this link a few days ago.
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by fleamour on 2012-02-21
Turns out to be a duff disk, formatting pushed it over the edge...

:D

---

### Post by fleamour on 2012-02-21
Yep!  Def dead disk.  Strange thing, it passed long/short GSmartControl tests but was demonstrating some very weird behaviour.  I hooked up to desktop tower via USB & could hear repeated clicking.

Dropped in a replacement I had lying around, auto mounts no annoying error prompt!  Works exactly as it should!

Still as ever, learned something.  Namely how to take ownership of mount points.

Cheerz!

\\:D/ :biggrin: \\:D/

---

