---
title: "chown, multiple users and a (hopefully shared) partition"
date: 2009-10-16
forum: General Help
---

### Post by Teabicky on 2009-10-16
I have set up a partition on an extra internal hard drive for me and my wife to use on separate accounts.  I can grant access to each user after log in using:

sudo chown -R *username* /*media*/*linux *

This works a treat until I log on as a different user, at which point the permissions are reset and I have to type the command again.  Is there any way round this?  I suspect that it could have something to do with "groups" but I am not too sure.

Thanks in advance for any suggestions/ advice/ links etc etc.

---

### Post by Teabicky on 2009-10-17
bump

---

### Post by StuartN on 2009-10-17
> **Teabicky said:**
> sudo chown -R *username /media/linux *

You are changing the owner of /media/linux, and recursively every file under it, to match the currently logged in user, and repeating this at every login.

Before you change the owner and group of the path (**chown :group path** or **chgrp group path**) to some group that all permitted users are a member of, you should decide which owner and group to use. Once you have chosen the owner:group, you can set permissions with a variation of **chmod -R ug+wrx path** - this version would ensure that the owner and all members of the group could read, write and execute every file under path.

Every new file and every edited file (because the revised version is a new file) will belong to the logged in user:primarygroup and have permissions according to the logged in user's current umask. The command umask shows the denials (0022 by default, deny write to group and others) while umask -S shows permissions. Also by default, every user's primary group is a group with their own username, with only one member - so user:user gets read, write and execute, members of the group user (just user) gets read and execute and others get read and execute.

You can change the primary group a user belongs to System->Administration->Users and groups and either join all users into a selected user's primary group, or create a new group.

You can change the default umask (eg to 0011, group and others can not execute) in the last line of /etc/profile.

*(You could also (not very Linux) format the partition to NTFS so that directories and files have no owner or permissions, and inherit them from the mount point according to which user mounts the partition.)*

---

### Post by Teabicky on 2009-10-17
O.k I have gone into S*ystem->Administration->Users and groups* and I think that I have set both my wifes and my primary group as "*users*".

I then ran the command **chmod -R ug+wrx /media/linux** followed by c**hown :users /media/linux**.  I still don't have permission to view or do anything else to the files on */media/linux*.  

What have I done wrong?

---

### Post by StuartN on 2009-10-17
> **Teabicky said:**
> I still don't have permission to view or do anything else to the files on */media/linux*.

If you run **ls -l /media/linux**, then what are the permission and ownership of the directory and the files? And any directory within /media/linux?

Hopefully you only need to ensure that you have group users with group permissions of wr(x). The commands **whoami** and **groups** are useful to check your identity and membership.

---

### Post by Teabicky on 2009-10-17
ls -l /media/linux =

> total 36
drwx------   3 dell users  4096 2009-10-14 22:40 **Dell**
drwx------ 499 dell users 20480 2009-10-06 10:05 **Music**
drwx------  54 dell users  4096 2009-10-11 11:12 **Pictures**
drwx------   5 dell users  4096 2009-10-11 11:10 **Rich**
drwx------   6 dell users  4096 2009-08-21 10:51 **Videos**


whoami = *rich* (whoami for mywife = dell)

users = *users adm dialout cdrom plugdev lpadmin admin sambashare*

---

### Post by StuartN on 2009-10-17
So you are both in group users, the directory belongs to dell and dell has wrx permissions while group and others have no permissions to do anything.

Your recursive **chmod -R ug+wrx /media/linux** did not work. Could you also **ls -l /media** to see who owns the mountpoint?

Is this an NTFS formatted partition? If so, then every directory and file has the ownership and permissions of the mountpoint.

---

### Post by Teabicky on 2009-10-17
*ls -l /media* =

> total 24
lrwxrwxrwx  1 root root      6 2009-09-24 12:39 **cdrom** -> cdrom0
drwxr-xr-x  2 root root   4096 2009-09-24 12:39 **cdrom0**
drwx------ 12 rich root  16384 1970-01-01 01:00 **EXTER 250GB**
drwxrwxr-x  9 dell users  4096 2009-10-14 22:40 **linux**

So that must mean dell:users owns the mount point.  If I run *sudo chown -R rich:users /media/linux* and then *ls -l /media* I get this:

> total 24
lrwxrwxrwx  1 root root      6 2009-09-24 12:39 **cdrom** -> cdrom0
drwxr-xr-x  2 root root   4096 2009-09-24 12:39 **cdrom0**
drwx------ 12 rich root  16384 1970-01-01 01:00 **EXTER 250GB**
drwxrwxr-x  9 rich users  4096 2009-10-14 22:40 **linux**


Also this is a ext4 partition.  I did have a fat32 that I used between windows and ubuntu but had the same problem with permissions.  So I divided the hard drive in two, one half is still fat32 which I use for windows and the other is the ext4 (/media/linux) in question.  Might it be easier to merge the hard drive back into one whole and format it as ntfs?

---

### Post by StuartN on 2009-10-17
> **Teabicky said:**
> If I run *sudo chown -R rich:users /media/linux* and then *ls -l /media* I get this:
drwxrwxr-x 9 rich users 4096 2009-10-14 22:40 linux

And I assume the same permissions and ownership of everything within the /media/linux partition? And that both users dell and rich can access all the files on it?

After running the recursive **chown -R** and **chmod -R** the ownership and permissions of the files should not change with logging in and remounting, only the ownership of the mountpoint /media/linux should change.

---

### Post by Teabicky on 2009-10-17
> **StuartN said:**
> And that both users dell and rich can access all the files on it?


This is the problem, "dell" doesn't have access to the files, unless I run the chown -R command again, but with "dell" instead of "rich".  After that "rich" is locked out and so on and on.

I was hoping that there was some way to run the chown command and include both users, but then that I what groups are for I suppose.

I am stumped,  I can still use the drive so it isn't a major problem but we do use dropbox and that doesn't like it.

---

### Post by ibuclaw on 2009-10-17
> **Teabicky said:**
> This is the problem, "dell" doesn't have access to the files, unless I run the chown -R command again, but with "dell" instead of "rich".  After that "rich" is locked out and so on and on.

I was hoping that there was some way to run the chown command and include both users, but then that I what groups are for I suppose.

I am stumped,  I can still use the drive so it isn't a major problem but we do use dropbox and that doesn't like it.

What filesystem does the partition use?

Certain filesystems support ACLs (Access Control Lists), which allow you to apply permissions on a **per user** basis, rather than owner/group/other.

Can you run:
```
cat /etc/fstab
```
And paste the output?

Regards
Iain

---

### Post by StuartN on 2009-10-17
> **Teabicky said:**
> This is the problem, "dell" doesn't have access to the files, unless I run the chown -R command again, but with "dell" instead of "rich".  After that "rich" is locked out and so on and on.

This is an EXT3 partition and your **ls -l /media** gives **drwxrwxr-x 9 rich users 4096 2009-10-14 22:40 linux**, meaning that the mountpoint /media/linux belongs to rich (at least just now), but all members of users have rwx access, in fact everyone has the default rx access.

Are you sure you recursed into /media/linux when you run chmod? Another **ls -l /media/linux** should show who owns the directories and files within it.

---

### Post by Teabicky on 2009-10-17
> **StuartN said:**
> 
Are you sure you recursed into /media/linux when you run chmod?

I am pretty sure that I did, this is the line that I used

> chmod -R ug+wrx /media/linux

tinevole, this is the output of cat /etc/fstab

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9e9b26a5-29ca-461d-b6c3-395a181de53c /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=4b4600af-ba7e-4531-9203-a5fdff153ce7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1	/media/linux	ext4	defaults	0	0

---

### Post by StuartN on 2009-10-17
> **Teabicky said:**
> tinevole, this is the output of cat /etc/fstab

```
/dev/sdb1 /media/linux ext4 defaults 0 0
```

Sorry, EXT4 not EXT3 - but that should not make any difference. You have a path with group ownership users, both users belong to that group and the group members have rwx permission.

Does that also apply to the directories within /media/linux?

---

### Post by ibuclaw on 2009-10-18
> **Teabicky said:**
> I am pretty sure that I did, this is the line that I used

tinevole, this is the output of cat /etc/fstab

FYI, you shouldn't need to use executable permissions on files that you will never plan on executing!

So, you have 2 options.

**Option 1)** The Unix Way

1) Change ownership recursively
```
sudo chown root:users /media/linux -R
```
2) Apply Set Group ID permissions to the directories.
```
sudo find /media/linux -type d -exec chmod 2775 "{}" \;
```
If you don't want the "Other" group to have Read and Traverse permissions, use **2770** instead.

3) Apply appropriate permissions on files that already exist.
```
sudo find /media/linux -type f -exec chmod 664 "{}" \;
```
You could use **660**, but if you applied the above, as "2770" then there will be no motivation to.

4) Add yourselves to the users group
```
gksudo gedit /etc/group
```
And you should set the line so it looks something like this:
```
users:x:100:**dell,rich**
```

Then logout/login your the permissions to take effect.


**Option 2)** The POSIX ACL Way

ACL stands for Access Control Lists. How ACLs differ from Unix permissions is that rather than "Owner -> Group -> Other" permissions, ACLs allow you to change permissions on a "**Per User**" basis. This has the downside to some overhead in accessing/writing files, but it's flexibility and benefits probably outweigh the cons.

1) Install Eiciel
```
sudo apt-get install eiciel acl
```
2) Mount the filesystem with ACL turned on
```
gksudo gedit /etc/fstab
```
Alter the mount line so it looks like this:
```
/dev/sdb1 /media/linux ext4 defaults**,acl** 0 0
```
Then remount the filesystem
```
sudo mount -o remount /media/linux
```
3) Now, launch the application:
```
gksudo eiciel
```
Select **Open** in the top right hand corner of the application, then select the "/media/linux" directory

4) Then add both "dell" and "rich" to the ACL as Users, then quit. (See screenshots of before and after)


In both methods, you should both be able to read/open each others documents, music, etc, but if one of your creates a file, the other won't be able to edit it. Reasons because Linux has no notion of "**Inheritance**". In Linux, if you apply a permission to the top directory, that permission stays on the top directory. This is contrary to Windows, where if you apply a permission on a top directory, it is applied to all child directories, unless "inheritance" is explicitly turned off. (If it isn't turned off, then Windows actively updates/enforces parent permissions on all child files/directories. Whether or not this is your expected behaviour is arguable, but there will be alot of overhead generated from it).

If this proves to be tedious in the long run, there is an alternative, and that is to use a filesystem that has no knowledge of Permissions (ie: NTFS or FAT). Then mount the filesystem with the umask 002, and the gid set to a common shared group. (As is the default with NTFS filesystems in Ubuntu).

Regards
Iain

---

### Post by Teabicky on 2009-10-18
Whoo! That's a lot to get my head round, but it all sounds good!  It's late on an Sunday evening and I am working late tomorrow so I won't try any of this till Tuesday.  Of course I will post the outcome here when I do.

One question I do have in the mean time though relates to this quote:

> You could use 660, but if you applied the above, as "2770" then there will be no motivation to. *by tinivole*

Is there anywhere that has a comprehensive list of what these numbers mean (660, 2770, 770, 777 etc. etc.), just so I can increase my understanding and have a reference point in the future?

Thanks

Rich

---

### Post by Lars Noodén on 2009-10-19
> **Teabicky said:**
> 
Is there anywhere that has a comprehensive list of what these numbers mean (660, 2770, 770, 777 etc. etc.), just so I can increase my understanding and have a reference point in the future?


These octal (base eight) numbers are another way of denoting r,w, or x.
Simplest permissions.  Some file systems support more advanced ACLs

```

Base 8:  421
Letter:  rwx

**rwx** = 4 + 2 + 1 = **7**
**r-x** = 4 + 0 + 1 = **5**
**rw-** = 4 + 2 + 0 = **6**
**r--** = 4 + 0 + 0 = **4**

and so on...

```

See explanations like this:
[http://www.math.hmc.edu/computing/support/permissions/](http://www.math.hmc.edu/computing/support/permissions/)

```

# User=    [COLOR="Sienna"]421[/COLOR]
# Group=      [COLOR="Green"]421[/COLOR]
# Everyone=      421
$ ls -l
          d[COLOR="Sienna"]rwx[/COLOR][COLOR="Green"]---[/COLOR]---  lars lars    4096 2009-10-19 11:27 eEcPzS
          d[COLOR="Sienna"]rwx[/COLOR][COLOR="Green"]r-x[/COLOR]r-x  lars web     1024 2009-10-19 13:05 foo
          l[COLOR="Sienna"]rwx[/COLOR][COLOR="Green"]rwx[/COLOR]rwx  lars lars      10 2009-10-19 12:43 bar -> /home/lars
          -[COLOR="Sienna"]rw-[/COLOR][COLOR="Green"]r--[/COLOR]r--  root root      10 2009-10-19 12:43 fstab
# octal equivalents 
          d[COLOR="Sienna"]7[/COLOR]  [COLOR="Green"]0[/COLOR]  0    lars lars    4096 2009-10-19 11:27 eEcPzS
          d[COLOR="Sienna"]7[/COLOR]  [COLOR="Green"]5[/COLOR]  5    lars web     1024 2009-10-19 13:05 foo
          l[COLOR="Sienna"]7[/COLOR]  [COLOR="Green"]7[/COLOR]  7    lars lars      10 2009-10-19 12:43 bar -> /home/lars
          -[COLOR="Sienna"]6[/COLOR]  [COLOR="Green"]4[/COLOR]  4    root root      10 2009-10-19 12:43 fstab



```

---

### Post by Teabicky on 2009-10-20
First of all I tried The POSIX ACL Way and all looked good.  Until I actually logged out and tried to use the directory with "dell".  No luck, I was in the same situation as before, despite eiciel indicating the contrary... baffling!

So, I tried the Unix way.........GOAL!!  It worked from the first attempt, so a big thanks to everybody who has helped me with this.

However in light of this (from tinivole):

> In both methods, you should both be able to read/open each others documents, music, etc, but if one of your creates a file, the other won't be able to edit it. Reasons because Linux has no notion of "Inheritance". In Linux, if you apply a permission to the top directory, that permission stays on the top directory. This is contrary to Windows, where if you apply a permission on a top directory, it is applied to all child directories, unless "inheritance" is explicitly turned off. (If it isn't turned off, then Windows actively updates/enforces parent permissions on all child files/directories. Whether or not this is your expected behaviour is arguable, but there will be alot of overhead generated from it).

If this proves to be tedious in the long run, there is an alternative, and that is to use a filesystem that has no knowledge of Permissions (ie: NTFS or FAT). Then mount the filesystem with the umask 002, and the gid set to a common shared group. (As is the default with NTFS filesystems in Ubuntu).

I think I might just go the NTFS route (sorry!!), if only to save me (and my wife) headaches in the future.  

At least I can mark this thread as solved!!

---

### Post by ibuclaw on 2009-10-20
> **Teabicky said:**
> First of all I tried The POSIX ACL Way and all looked good.  Until I actually logged out and tried to use the directory with "dell".  No luck, I was in the same situation as before, despite eiciel indicating the contrary... baffling!

So, I tried the Unix way.........GOAL!!  It worked from the first attempt, so a big thanks to everybody who has helped me with this.

However in light of this (from tinivole):



I think I might just go the NTFS route (sorry!!), if only to save me (and my wife) headaches in the future.  

At least I can mark this thread as solved!!

FYI, this is what rwx have affect on:
[LIST]
[*]**Directories:**
**r** - allows you to list files/folders in the directory (useless if you cannot traverse).
**w** - allows you to mk and rm files/folders in the directory.
**x** - allows you to traverse into the directory (but not list files).
[*]**Files:**
**r** - allows you to read a file.
**w** - allows you to append/truncate a file.
**x** - allows you to execute a file (useless if you cannot read).
[/LIST]

Regards
Iain

---

