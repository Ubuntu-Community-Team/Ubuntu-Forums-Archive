---
title: "Sticky bit or ACL for group inheritance."
date: 2012-08-16
forum: General Help
---

### Post by artheus on 2012-08-16
Hi,

I've understood that you can use either the Sticky bit or the ACL for making new sub-directories  and files created in a main directory get the same group ownership as the main directory.

For example:

 &#8226; Note! chmod permissions of all files and directories in this example is 770
 &#8226; Note! my filesystem type is ext4. And my fstab setting of it is "defaults,acl".

If I have got a directory i call "/var/foo" and that will somewhat act as an collaborative platform for all the server users which are members of the group "bar". The ownership of the folder "/var/foo" is "root:bar".

The problem I'm first facing as I am setting up this environment is that whenever a user creates a file or a directory the owner of that file/dir is by both group and user that specific user. (Eg. the user 'albert' creates a sub-directory in the directory /var/foo and the ownership of that directory is "albert:albert" ).

What I want to happen is that the ownership of that sub-directory should be "albert:bar", so all other users that are members of the group "bar" should be able to edit, rename, unlink and execute all the contents of "/var/foo" at all times.

I've been searching for solutions of this. I've found two methods that seems to work.
Some people tell me to use ACL for this, by using the "setfacl"-command I can achieve this.
Other people tell me to use the sticky bit SGID method, by simply running the command "chmod -R 2770 /var/foo", for achieving this.

I am very curious to which method is actually preferred, and why it is preferred?
Is it a question of taste? What are the pros and/or cons?
Does any of these alternatives pose as a threat to security?
Are there any more alternatives to this?

Thankful for any feedback!

Cheers,
Artheus

ADDITION: I can see that by using the chmod permission of 2770 on the directory "/var/foo" gives all new sub-deirectories the same permissions. Creating a new file with this method will instead follow the systems default umask and the files get the chmod permissions of "-rw-rw-r--" which is not at all desired, by me. Any thoughts?

---

### Post by SlugSlug on 2012-08-16
setfacl allows you to add many permissions like
group1:rwx
group2:rx
group3:r
user1:rwx


etc

---

### Post by bab1 on 2012-08-16
> **artheus said:**
> Hi,

I've understood that you can use either the Sticky bit or the ACL for making new sub-directories  and files created in a main directory get the same group ownership as the main directory.

For example:

 &#8226; Note! chmod permissions of all files and directories in this example is 770
 &#8226; Note! my filesystem type is ext4. And my fstab setting of it is "defaults,acl".

If I have got a directory i call "/var/foo" and that will somewhat act as an collaborative platform for all the server users which are members of the group "bar". The ownership of the folder "/var/foo" is "root:bar".

The problem I'm first facing as I am setting up this environment is that whenever a user creates a file or a directory the owner of that file/dir is by both group and user that specific user. (Eg. the user 'albert' creates a sub-directory in the directory /var/foo and the ownership of that directory is "albert:albert" ).

What I want to happen is that the ownership of that sub-directory should be "albert:bar", so all other users that are members of the group "bar" should be able to edit, rename, unlink and execute all the contents of "/var/foo" at all times.

I've been searching for solutions of this. I've found two methods that seems to work.
Some people tell me to use ACL for this, by using the "setfacl"-command I can achieve this.
Other people tell me to use the sticky bit SGID method, by simply running the command "chmod -R 2770 /var/foo", for achieving this.

I am very curious to which method is actually preferred, and why it is preferred?
Is it a question of taste? What are the pros and/or cons?
Does any of these alternatives pose as a threat to security?
Are there any more alternatives to this?

Thankful for any feedback!

Cheers,
Artheus

ADDITION: I can see that by using the chmod permission of 2770 on the directory "/var/foo" gives all new sub-deirectories the same permissions. Creating a new file with this method will instead follow the systems default umask and the files get the chmod permissions of "-rw-rw-r--" which is not at all desired, by me. Any thoughts?

The above is NOT setting the sticky bit.  It is setting the SGID bit.  If you set the SGID bit on a directory (i.e. /var/foo), then all directories and files below will have the inherited group that you set.  To change the *default* permissions upon you need to change the **umask**.  What do you see as wrong with rw-rw-r-- (umask 0002)?

Edit:  I would use ACL's only for exceptions.  It gets confusing otherwise.

Edit2: Questions of preference come down to the sysadmin control,  No matter how you get to the permissions on a specific file or directory, it is still a matter of permissions granted.  That can be a political decision rather than a technical one.  Most of the time the SGID bit and group assignment will take care of the need.  On the other hand ACL's can help when you need to add or subtract permissions for particular users.

---

### Post by artheus on 2012-08-16
> **bab1 said:**
> The above is NOT setting the sticky bit.  It is setting the SGID bit.  If you set the SGID bit on a directory (i.e. /var/foo), then all directories and files below will have the inherited group that you set.  To change the *default* permissions upon you need to change the **umask**.  What do you see as wrong with rw-rw-r-- (umask 0002)?

Edit:  I would use ACL's only for exceptions.  It gets confusing otherwise.

Edit2: Questions of preference come down to the sysadmin control,  No matter how you get to the permissions on a specific file or directory, it is still a matter of permissions granted.  That can be a political decision rather than a technical one.  Most of the time the SGID bit and group assignment will take care of the need.  On the other hand ACL's can help when you need to add or subtract permissions for particular users.

Thank you! Wonderful answers!

I guess I've misinterpreted the meaning of the sticky bit. I thought that the sticky bit, the SGID and the SUID was all the same as it is set byte the value of the first byte of a chmod call, if the chmod calls mode parameter contains 4 numeric values. I have now read more about that in [this blogpost]("http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php"). ( Thanks you for the tip. )

The thing that worries me with the rw-rw-r-- is that that will give all users in the system a read-permission. What if the data in the collaboration-folder is very sensitive, and shall not be read by any other users than the ones in the "bar"-group?

By changing the umask, doesn't that mean that that will be changed globally? Or kan I actually do this per-directory? If setting the umask is only globally, are there an alternate way of achieving this?
Searching the net for this gives me answers like "Use bindfs!" or "Maybe you should set up a cron job to handle this for you?" which for me seems quite undesirable. For bindfs, I guess I'd have to re-run the command on every restart? And a cron job is not live, which I'd really like it to be.

When you say that you would use ACL's only for exceptions, and that it would otherwise get confusing. How do you mean it would get confusing? Confusing for me as a system administrator or confusing for the users? In what way will it become confusing? ( I do not doubt your statement. I am only curious. )

Again, Thanks!

Cheers,
Artheus

---

### Post by LewisTM on 2012-08-16
There is a nice tutorial [here]("http://brunogirin.blogspot.ca/2010/03/shared-folders-in-ubuntu-with-setgid.html") on how to combine the setgid bit and ACLs to achieve what your are seeking.

To emulate a local umask for a directory tree, you must set default ACLs.
```
setfacl -R -d -m u::rwx,g::rwx,o::--- folder
```
This will remove access rights to other users for newly created files. Be aware that it will not remove EXISTING permissions nor will it force permissions for files that are moved or copied into the directories.

Cheers!

---

### Post by bab1 on 2012-08-17
> **artheus said:**
> Thank you! Wonderful answers!

I guess I've misinterpreted the meaning of the sticky bit. I thought that the sticky bit, the SGID and the SUID was all the same as it is set byte the value of the first byte of a chmod call, if the chmod calls mode parameter contains 4 numeric values. I have now read more about that in [this blogpost]("http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php"). ( Thanks you for the tip. )
The chmod value is in bits not bytes. Each "slot" handles the value for its specific permission.  These slots are:  [COLOR="Red"]extended[/COLOR]-[COLOR="Blue"]user[/COLOR]-[COLOR="Green"]group[/COLOR]-[COLOR="Purple"]others[/COLOR].  Each slot is 3 bits wide.  Using the SGID bit as an example; the bit would be the 2nd bit in the extended slot that is flipped (010).  If you wanted that to be the SUID it would be the 3rd bit flipped (100) Note: we read from right to left for bits.  See [**[COLOR="DarkSlateGray"]here[/COLOR]**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for details.> 

The thing that worries me with the rw-rw-r-- is that that will give all users in the system a read-permission. What if the data in the collaboration-folder is very sensitive, and shall not be read by any other users than the ones in the "bar"-group?

A lot of the worries that you have can be handled by thoughtful engineering (design).  In the case of Linux and umask, the default permissions are 777 for directories and 666 for files.  The umask just modifies that to what the the sysadmin wants.  Why the directory has the execute bit set is important.  Linux uses the execute bit to allow the user to descend or traverse directory.  This means that if you set the permissions to 770 on the root directory that you wish to protect (i.e. /var/foo) nothing below is world readable.  To restate that:  If you assign the permissions 2770 and the ownership of root:*mygroup* to the directory /var/foo, then only the users in the group *mygroup* and root can descend into or traverse the directory /var/foo.  No access to others.  The default umask will still allow the default permissions upon creation of files and directories.  > 

By changing the umask, doesn't that mean that that will be changed globally? Or kan I actually do this per-directory? If setting the umask is only globally, are there an alternate way of achieving this?
Searching the net for this gives me answers like "Use bindfs!" or "Maybe you should set up a cron job to handle this for you?" which for me seems quite undesirable. For bindfs, I guess I'd have to re-run the command on every restart? And a cron job is not live, which I'd really like it to be.
You can't set umask on a per directory basis, but you can set the umask per mounted partitions (ext2/3/4).  If I was to have a server that is being dedicated to a group project, I would seriously consider using a partitioned disk and mounting it into the servers file system at the appropriate place.> 
When you say that you would use ACL's only for exceptions, and that it would otherwise get confusing. How do you mean it would get confusing? Confusing for me as a system administrator or confusing for the users? In what way will it become confusing? ( I do not doubt your statement. I am only curious. )
...
I don't like using ACL's unless it is an exception.  This is needless complication most of the time.  You have to document it and someone after you has to know to look for the documentation to understand your reasons for using the ACL's.  That being said, when you need them, ACL's work brilliantly.  +1 for @LewisTM's post.  Lots of good information there.

---

