---
title: "NFS - no group access?"
date: 2012-05-03
forum: General Help
---

### Post by RogerTX on 2012-05-03
I'm running 10.04 (I think - the LTS version).

I have a NAS and have it NFS mounted on Ubuntu.

What I want to is give my wife and I permissions to make changes on the NAS shared music, and the kids get read-only access...

So, I created users

roger, ID=1001
rogerwife, ID=1002
kid1, ID=1003
kid2, ID=1004

On the NAS, I set up accounts for roger and rogerwife with the same UIDs.  I created a group (150) for "nasadm" and made my wife and I as members of that group.  I created the same group ID on the NAS and on Ubuntu.

Then I went to the NAS music folder, and changed the owner of all files & directories to "root" with group "nasadm".  Permissions were set to 2775 for folders, and 664 for files.

I thought this should work, and it does when I log onto the NAS server, but when I cd to "shared/music/folder1" and do "touch testfile", I get permission denied.  I have to make "folder1" owned by "roger" before it will let me make any changes.

So, what have I forgotten??

By the way, my user id is a member of MANY groups - they don't all need to be defined on the server, do they?  I assumed as long as "nasadm" used the same GIDs on the server and client that I'd be fine.

Another thing I want to try (but haven't yet) is to change my primary group away from "users" to "nasadm" to see if that works.

---

### Post by sandyd on 2012-05-03
> **RogerTX said:**
> I'm running 10.04 (I think - the LTS version).

I have a NAS and have it NFS mounted on Ubuntu.

What I want to is give my wife and I permissions to make changes on the NAS shared music, and the kids get read-only access...

So, I created users

roger, ID=1001
rogerwife, ID=1002
kid1, ID=1003
kid2, ID=1004

On the NAS, I set up accounts for roger and rogerwife with the same UIDs.  I created a group (150) for "nasadm" and made my wife and I as members of that group.  I created the same group ID on the NAS and on Ubuntu.

Then I went to the NAS music folder, and changed the owner of all files & directories to "root" with group "nasadm".  Permissions were set to 2775 for folders, and 664 for files.

I thought this should work, and it does when I log onto the NAS server, but when I cd to "shared/music/folder1" and do "touch testfile", I get permission denied.  I have to make "folder1" owned by "roger" before it will let me make any changes.

So, what have I forgotten??

By the way, my user id is a member of MANY groups - they don't all need to be defined on the server, do they?  I assumed as long as "nasadm" used the same GIDs on the server and client that I'd be fine.

Another thing I want to try (but haven't yet) is to change my primary group away from "users" to "nasadm" to see if that works.
Why don't you use IP addresses instead of groups?
Much easier and cleaner.

---

### Post by RogerTX on 2012-05-03
> **sandyd said:**
> Why don't you use IP addresses instead of groups?
Much easier and cleaner.

What do you mean? We have shared computers... or pretend we are talking about pictures, and not music.

---

### Post by yeahimthatguy on 2012-05-03
I've had similar issues. Adding myself to the group didn't work, but having that group as the primary group worked.

usermod -g groupname userid

---

### Post by RogerTX on 2012-05-03
> **yeahimthatguy said:**
> I've had similar issues. Adding myself to the group didn't work, but having that group as the primary group worked.

usermod -g groupname userid

That's excellent to know; that was going to be my next step.  Thanks for letting me know it (will probably) work.

I'll probably just "sudo vi /etc/passwd" to change the default group.

---

### Post by bab1 on 2012-05-03
> **RogerTX said:**
> That's excellent to know; that was going to be my next step.  Thanks for letting me know it (will probably) work.

I'll probably just "sudo vi /etc/passwd" to change the default group.

No need to change the primary group.  I successfully use a group strategy that uses BSD style group permissions.

I have all users that need to access the the directory in a common group.  I have the umask set to 0002.  This sets the default system create to 0775 for directories and 0664 for files.  

Then I set the directory in question to 3775.  This means that whenever you create a file or directory the group is set as the one defined in that root directory.  This in effect is how BSD manages groups (e.g based on the group not the owner (user)).  I have set the sticky bit but I don't know that it really matters.

At this point you can access the directory make files and subdirectories and so can the other users in the group.

You do not have worry about primary groups.  It really is more a matter of controlling the permissions of items created in the first directory.   Here is what my shared folder looks like ```
drwxrwsr-t 8 bab smbusers 4.0K 2012-04-15 18:40 share
```

Here are some files inside that shared directory```

-rw-rw-r--  1 bab  smbusers 2.4M 2011-05-30 16:18 Time After Time.mp3
-rw-rw-r--  1 egb  smbusers 3.0M 2011-05-01 17:41 boats.jpg
-rw-rw-r--  1 ajo  smbusers 634K 2011-05-02 07:39 scan1.jpg

```

Membership in the group *smbusers* controls access.  Note how all the files have 0664 permissions.

---

### Post by twipley on 2012-05-03
Also usable (adds user to group):
```
sudo adduser <user> <group>
```

---

### Post by yeahimthatguy on 2012-05-04
> **bab1 said:**
> No need to change the primary group.  I successfully use a group strategy that uses BSD style group permissions.

I have all users that need to access the the directory in a common group.  I have the umask set to 0002.  This sets the default system create to 0775 for directories and 0664 for files.  

Then I set the directory in question to 3775.  This means that whenever you create a file or directory the group is set as the one defined in that root directory.  This in effect is how BSD manages groups (e.g based on the group not the owner (user)).  I have set the sticky bit but I don't know that it really matters.

At this point you can access the directory make files and subdirectories and so can the other users in the group.

You do not have worry about primary groups.  It really is more a matter of controlling the permissions of items created in the first directory.   Here is what my shared folder looks like ```
drwxrwsr-t 8 bab smbusers 4.0K 2012-04-15 18:40 share
```

Here are some files inside that shared directory```

-rw-rw-r--  1 bab  smbusers 2.4M 2011-05-30 16:18 Time After Time.mp3
-rw-rw-r--  1 egb  smbusers 3.0M 2011-05-01 17:41 boats.jpg
-rw-rw-r--  1 ajo  smbusers 634K 2011-05-02 07:39 scan1.jpg

```

Membership in the group *smbusers* controls access.  Note how all the files have 0664 permissions.

Question. What do you mean when you say the "first directory"?

My issue was that I had files in a directory that was NFS mounted. The weird thing was that both of the owners were a group that I created, which the user was assigned to. Even then, the user that was added to that group could not have access to create files or create directories.

---

### Post by bab1 on 2012-05-04
> Question. What do you mean when you say the "first directory"?
By that I mean the root directory of your export (NFS) file system.  For example if you exported */nfs*, everything below that will be a distinct file system for this discussion.  The root of that file system is */nfs*.  Of course if you were to export /srv/nfs, then /srv/nfs would be the root of the file system.> 

My issue was that I had files in a directory that was NFS mounted. The weird thing was that both of the owners were a group that I created, which the user was assigned to. Even then, the user that was added to that group could not have access to create files or create directories. 
A directory can only have one owner and one group.  As I said, if you manage the permissions of the group correctly then any user who is part of that group can rw in the directory.  Is the directory (The mount point) set up to allow that?  Can you post that information (ls -l)?  A picture is worth a 1000 words.

---

