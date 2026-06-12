---
title: "Help with Permissions"
date: 2011-05-23
forum: General Help
---

### Post by steevven1 on 2011-05-23
COMPLETE EDIT FOR SIMPLICITY AND CLARITY:

Let me make this very simple. I have a directory. I want all files inside of it to have some particular permissions (let's say 777 plus the sticky bit), always, without exception, unless someone came in and changed them by hand.

In other words, I want files written to this directory to have a particular set of permissions, IGNORING the user's (and system default) umask.

The best way I came up with to do something close is to have a CRON job set the permissions once a minute, which is awful and even causes errors in programs occasionally.

Thanks for the help!

---

### Post by linuxinstalledfromhdd on 2011-05-23
try chmod 777 on that share directory and see if you like the result better. hopefully you have some user security in place at this point.

---

### Post by steevven1 on 2011-05-23
> **linuxinstalledfromhdd said:**
> try chmod 777 on that share directory and see if you like the result better. hopefully you have some user security in place at this point.


I don't think you understand. I need all files, including newly-written files from now till forever to have the specified permissions. I need this directory to override the default umask (and the user's umask). I don't need to set the permissions once; I know how to do that. Thanks.

---

### Post by steevven1 on 2011-05-23
Okay, I completely rewrote the post to be short and sweet. I think I have explained myself better now. Thanks for any help!

---

### Post by 3rdalbum on 2011-05-23
I'd like to know, too - my server currently uses a ten-secondly script to keep changing the permissions of everything in a folder. Not efficient, and while it works problem-free I'd like to know a less kludgy solution.

---

### Post by steevven1 on 2011-05-24
Bump.

---

### Post by Morbius1 on 2011-05-24
I can get you almost all the way there. The following will produce a directory that will allow all members of a particular group to add to and delete from the directory and edit all the files within it:

Let's say the folder is /home/Common

Change the group to plugdev:
```
sudo chown :plugdev /home/Common
```Change permissions:
```
sudo chmod 2775 /home/Common
```Edit /etc/profile as root and change the bottom line to:
```
umask 002
```If you added users to your system through "Users and Groups" than all of them are members of plugdev by default. The "2" in "chmod 2775" is the setgid bit and will force all saved files to "inherit" the group of the directory. Changing the global umask from 022 to 002 will force every saved folder / file to save with permissions of 775 / 664. So all users who are members of the group will have read / write access to all new folders / files.

You will need to logoff and login again for the umask change to take affect.

You could carry this to the extereme and set umask to 000 but that's insane. 

If that's still not far enough especially if you were serious about having all files have 777 - not just folders - then I would suggest bindfs:
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by 3rdalbum on 2011-05-28
I believe I've found a solution; it works for a Samba share (which is what I wanted the solution for) but if you want it for users on the same machine you could have them mount the Samba share.

The solution is to add a line to your smb.conf file, where it specifies the share:

```
guest only = yes
```

Make sure you comment-out any lines about "valid users" in this particular part of the file; the 'system-config-samba' program likes to add those lines. Also make sure "read only = no" is set; basically, make sure it's all logical and won't confuse Samba.

Also, earlier on in the file (in the section "global") there's a line that's currently commented-out about "guest account". Change it to read:

```
guest account = <desired username>
```

In my instance, it says "guest account = chris" because that's the name of the account that already owns all the files on the hard drive.

Either wait a minute or run the following command:

```
sudo service smbd restart
```

for the changes to take effect.

Anyone who attempts to log into the share, whether as a user or guest, will be logged in as guest. The guest account will actually be reading, writing and modifying files in the adopted user account (in my case, the 'chris' account).

---

### Post by bodhi.zazen on 2011-05-28
> **steevven1 said:**
> I don't think you understand. I need all files, including newly-written files from now till forever to have the specified permissions. I need this directory to override the default umask (and the user's umask). I don't need to set the permissions once; I know how to do that. Thanks.

The best solution is a cron job. Running one a minute seems a bit excessive ;)

Are you sure you need permissions of 777 ? For files why not 644 or 666 ?

---

