---
title: "Owner and group permissions help"
date: 2009-11-20
forum: General Help
---

### Post by Icey7 on 2009-11-20
Hi, I need a little help so without boring you by going into too much detail lets say I have a folder called "Downloads" which has owner "apple" and group "orange".

If group "orange" creates a subdirectory inside "Downloads" then "orange" becomes both the owner and group for this new subdirectory.

I know I can change the owner of the subdirectoy using:
sudo chown -R apple Downloads
But then I would have to do this every time "orange" creates a subdirectory.

So, is there a way for me to make sure every time "orange" creates a subdirectory that "apple" is always the owner?

Thanks!

---

### Post by bab1 on 2009-11-20
> **Icey7 said:**
> Hi, I need a little help so without boring you by going into too much detail lets say I have a folder called "Downloads" which has owner "apple" and group "orange".

If group "orange" creates a subdirectory inside "Downloads" then "orange" becomes both the owner and group for this new subdirectory.

This doesn't sound like correct behavior.  Groups don't create files or directories.  Users in the groups create them. The ownership should be to the user. > 

I know I can change the owner of the subdirectoy using:
sudo chown -R apple Downloads
But then I would have to do this every time "orange" creates a subdirectory.

So, is there a way for me to make sure every time "orange" creates a subdirectory that "apple" is always the owner?

Thanks!
Yes you can use UID/GID sticky bits for files and directories under the root directory that you are dealing with (i.e. the directory *apple*.

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.mepis.org/node/11040") and [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml").

---

### Post by doas777 on 2009-11-20
> **bab1 said:**
> 
See [**_[COLOR=DarkSlateGray]here[/COLOR]_**]("http://www.mepis.org/node/11040") and [**_[COLOR=DarkSlateGray]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml").
howdy,

I've had simmilar questions of late and was glad to see this come up.
the links expressed some ambiguity (words like 'may') on whether a file created by a user within a directory that has sgid set on it, will assume the group ownership of the dir's group owner, or the primary group of the user. has anyone used it on ubuntu and can confirm that behavior? it would be great if it works!

---

### Post by bab1 on 2009-11-20
> **doas777 said:**
> howdy,

I've had simmilar questions of late and was glad to see this come up.
the links expressed some ambiguity (words like 'may') on whether a file created by a user within a directory that has sgid set on it, will assume the group ownership of the dir's group owner, or the primary group of the user. has anyone used it on ubuntu and can confirm that behavior? it would be great if it works!

I have indeed.  I have set my /smb directory to 3644 and use the samba *force create* parameter with 3664 also.  I use force group to maintain control of the group ownership of files and directories in the file system also.  This is applying the sticky bit and the setGUID on the file permissions.

This means when a file is created the user is whom ever created it and the group is always the same.  As I am using this on Samba shares, I use a group called smbusrs.  Anyone who has permission (e.g. valid user) is in the smbusers group.

Edit: doas777, no may in the first link; the second link there are 3.  None refer to whether the extended chmod works.

The first *may *refers to whether a bit is on or off.  It may be either, but not both.

The second *may* is the notion that you MAY run across 4 non-zero values for the file permission.  You might not.  When this happens the leading (extended value) is an implied zero (e.g 644 is the same as 0644).

The third *may *is used when the author is referring to the file permissions the admin of the web server sets he may set them one way...or not.

---

### Post by doas777 on 2009-11-20
> **bab1 said:**
> I have indeed.  I have set my /smb directory to 3644 and use the samba *force create* parameter with 3664 also.  I use force group to maintain control of the group ownership of files and directories in the file system also.  This is applying the sticky bit and the setGUID on the file permissions.

This means when a file is created the user is whom ever created it and the group is always the same.  As I am using this on Samba shares, I use a group called smbusrs.  Anyone who has permission (e.g. valid user) is in the smbusers group.

sweet! that is pretty much my usecase. Thanks!

---

### Post by bodhi.zazen on 2009-11-20
The alternate to this is acl

[[ubuntu] Permissions on files in specific directory and subdirectories - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=939377") 

[How to share directories between groups of users using ACL - openSUSE]("http://en.opensuse.org/How_to_share_directories_between_groups_of_users_using_ACL") 

If you wish there is a gui (it is in the repos)

[Linux.com :: Smart ACL management with Eiciel]("http://www.linux.com/feature/138169") 

And there are some options server side for the behavior of samba shares as well (see teh samba documentation).

---

### Post by Icey7 on 2009-11-22
Thanks for the help - I should probably explain that I am a linux neophyte. I read throught the UID/GID stickybit links and think I understand how it should work but have been unsuccessful so far.

I used the command:
sudo chmod -R x777 Downloads [where "x" is the octal UID/GID/Sticky operand]
and in the end tried every value from 1 to 7 for "x".

When "x" was set to 4 I was able to delete the directory created within Downloads but again only after the directory had been created. Any subsequent directorys created by the group/user "orange" could not be deleted by "apple" as this user is neither the owner nor group.

Am I making some basic mistake in my command or have I got this completely wrong?

Thanks!

---

### Post by bodhi.zazen on 2009-11-22
With the sticky bit set, only the owner of a file can delete it. Others can rw the file , bu t they all need to be in the group that owns the directory.

I bellieve you would be happier with ACL, see the links I gave you.

Depending on your file system, you need to enable acl by editing fstab ( /etc/fstab ) and rebooting. (well you do not *need* to reboot, you can remount).

See also : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

add "acl" (without quotes) to the options (4th) column.

---

