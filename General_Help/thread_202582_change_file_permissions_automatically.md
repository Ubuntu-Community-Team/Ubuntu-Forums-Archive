---
title: "change file permissions automatically?"
date: 2006-06-23
forum: General Help
---

### Post by dspivey on 2006-06-23
I have a shared folder that I use for sharing files with other users on the network (obviously), but I also allow them to place files into that folder; it works kind of like a scaled-down file server.  I've noticed that sometimes when other users place files in that folder the permissions of that file are set to something that may not allow another user on the network to edit or even open the file.  When that happens I 'chmod 777' the problem file to allow all users read/write permissions.  I'd like to know if there is a way I can set the shared folder to automatically change the permissions of all files that are placed into it.  Thanks in advance for any advice!

---

### Post by aysiu on 2006-06-23
[This](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) should help.

---

### Post by rivalarrival on 2007-09-14
Perhaps I'm just insane, but I've got a similar problem after following that guide.

I've sharing a folder with Samba for my remote windows users (accessing it with a pptp  connection to another server on the network) 

I want to use SSH instead of Samba for me (and any new Linux users) but it doesn't seem like new files are inheriting the ACL permissions.

fstab entry  had "umask=0007" option set (worked local, but not for sshfs) 
ACL sets group permissions to rw (works local, not for sshfs)

It's like doing it through sshfs overrides everything!

Any thoughts would be greatly appreciated...

---

### Post by psusi on 2007-09-14
Put the users in a group, make that group own the directory, then set the group sticky bit ( chmod g+s ) on the directory, which will cause new files to be owned by that group.

---

### Post by rivalarrival on 2007-09-15
> **psusi said:**
> Put the users in a group, make that group own the directory, then set the group sticky bit ( chmod g+s ) on the directory, which will cause new files to be owned by that group.

Tried that, no such luck. I had already switched our profiles to default to the "users" group and ls -l reports that everything is owned by dave:users. But, although they are owned by users, users group has no permissions.  

/etc/fstab entry: 
/dev/hdb1   /mnt/filestore   ext3   defaults,acl  0 0

sudo setfacl -Rdm g:users:rwx /mnt/filestore
used places > connect to server... to setup an SSH share to that folder from another machine
copied a local .jpg to /mnt/filestore/testing/P1040718.JPG on remote server

Here's what getfacl has to say now:

```


$ getfacl /mnt/filestore
getfacl: Removing leading '/' from absolute path names
# file: mnt/filestore
# owner: dave
# group: users
user::rwx
group::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:users:rw-
default:mask::rwx
default:other::r-x

$ getfacl /mnt/filestore/testing
getfacl: Removing leading '/' from absolute path names
# file: mnt/filestore/testing
# owner: dave
# group: users
user::rwx
group::rwx                      #effective:r-x
mask::r-x
other::r-x
default:user::rwx
default:group::rwx
default:group:users:rw-
default:mask::rwx
default:other::r-x

$ getfacl /mnt/filestore/testing/P1040718.JPG
getfacl: Removing leading '/' from absolute path names
# file: mnt/filestore/testing/P1040718.JPG
# owner: dave
# group: users
user::rwx
group::rwx                      #effective:---
group:users:rw-                 #effective:---
mask::---
other::---

$ touch /mnt/filestore/testing/test.file
$ getfacl /mnt/filestore/testing/test.file
getfacl: Removing leading '/' from absolute path names
# file: mnt/filestore/testing/test.file
# owner: dave
# group: users
user::rw-
group::rwx                      #effective:rw-
group:users:rw-
mask::rw-
other::r--



```

Come on, folks, I know I'm doing something dumb - point out my stoopid so I can laugh too!

Edit:

Uh Oh...  sshfs doesn't support ACLs (YET!!)...  I can't brain today, I'm has the dumb.
[http://www.howtoforge.com/sshfs_rdiff_backup](http://www.howtoforge.com/sshfs_rdiff_backup)

---

### Post by psusi on 2007-09-15
So the files are owned by the users group, and the users are in that group... what are the permissions on the file according to ls -l?  By default they should at least be readable by the group.  If not, you can change your umask to adjust the default file mode.

---

### Post by rivalarrival on 2007-09-15
ls -l reports -rwx------ permissions for any of the new files I drop into the sshfs folder on the local machine.

Tried setting umask to 0007 in fstab...  Worked local, (or from an SSH terminal window to the remote machine - touching a file to create it would leave it with rwxrwx---) but it wouldn't work for files written via the sshfs share on my local machine.  When using my sshfs share, whatever permissions the files had on my local machine they maintain when written to the remote machine. 

Regardless of fstab umask. 

Regardless of ACL.


The link in my last post suggests that this is a known issue with sshfs, leading me to believe that sshfs was never intended for this application. The more I think about it, the less I want to use it... :)

Really, the only reason I was trying to use sshfs is because I need a simple, somewhat-secure, internet accessible file server that plays nice with both Windows and Linux clients. Right now I'm using samba over pptp for the windows side, but sshfs seemed nearly twice as fast for the linux boxes, and only slightly slower over puTTY on the Windows machines. 

A secure FTP server is probably the best solution, but my only experience with ftp servers was with IIS on an old W2K server and organic windows clients- we did away with that REAL quick, about 3 years ago - mapping network drives and network folders to an ftp share simply sucked. Writing files was erratic, moving or deleting them didn't work right either; stale files would exist for the clients but not at the server... I just assumed it was the ftp protocol itself and switched to Windows file sharing over pptp.

Linux seems much more well behaved - I've been using vsftpd as a workaround for the sshfs issues, (permissions seem to apply appropriately with either Samba or FTP)  I think I'll just spend some time tightening up the ftp server and call it a day.

---

### Post by Zill on 2007-09-15
Don't know if this is what you want but it works for me...
Default umask is set to 022.
Edit file /etc/profile and change umask from 022 to 002
umask does not immediately change
Logout and login again
New file permissions = 664
New directory permissions = 775

---

### Post by rivalarrival on 2007-09-15
Thought about that, but that's a global change and even if it works, (which seems doubtful for sshfs - fstab umask for the partition did nothing) it will have affects beyond simply fixing this issue. It would also break (or at least weaken security) on other folders...  The ONLY place I want 770 permissions enforced is on this partition (/dev/hdb1, mounted as /mnt/filestore)

Thanks, though!  The solution seems to be "Don't use sshfs for this purpose" - I can deal with that.

---

### Post by oschonrock on 2007-09-20
you might want to consider the solution referred to here:

[http://osdir.com/ml/file-systems.fuse.sshfs/2006-05/msg00008.html](http://osdir.com/ml/file-systems.fuse.sshfs/2006-05/msg00008.html)

ie (the link is slightly out of date):

[http://www.gnuarch.org/gnuarchwiki/Centralized_Development](http://www.gnuarch.org/gnuarchwiki/Centralized_Development)

---

