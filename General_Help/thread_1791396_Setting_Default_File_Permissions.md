---
title: "Setting Default File Permissions"
date: 2011-06-26
forum: General Help
---

### Post by Kissell on 2011-06-26
I have a file server running a cronjob to reset file permissions on a regular basis.  I was thinking, I wonder if there is a way to do the chmod and chown command in a single command, as I always have to do both on the same folder, the way that you can do "chown root:users Uploads" instead of having to do two separate commands for chown and chgrp.  

Then I got to thinking, are these commands even necessary?  Every file copied or moved into these folders by any user needs to be something like "chmod 750" and "chgrp root:users", so rather than running a cronjob to do these modifications at regular intervals, there ought to be a way to set the folder permissions so that any files contained within will have these permissions.  

The problem arises because users create documents, then a supervisor with elevated privileges can move those documents into a shared folder, however the permissions are wrong, they are user1:user1 for the owner and group and the other users can't read the file until a cronjob changes the group to be users.  This has actually been acceptable, but certainly there is a better way to do this.  Anyone know?  TIA

---

### Post by Morbius1 on 2011-06-26
The "chgrp root:users" part can be done with a setgid:

```
sudo chmod 2770 root:users /path/to/shared/folder
``` The "2" will force all new files / subfolders saved to that folder to "inherit" the group "users".
[COLOR=Blue]**EDIT: The command above makes no sense. Please see correction below.**[/COLOR]

You can change it to a "chmod 3770" is you want the same thing as above but you only want root and the original owner to be able to delete it.

As for this:
 > Every file copied or moved into these folders by any user needs to be something like "chmod 750" I don't know of anything other thatn a chmod that could force linux to set a file to be executable by default. Even if you wanted 640 it would require a change to the umask parameter in /etc/profile to 026 but then it would apply to every new file everywhere on the system. Maybe someone else has a solution to that one.

---

### Post by Kissell on 2011-06-26
I remember doing something like this in the past on another file server several years ago, and used umask to set a particular folder to change default permissions of new files put in it, but I can't remember how I did it.

Changing everything on the system to 640 would be bad...  But if I could change everything new put into a folder and its subfolders starting from a specific path, that would be perfect.  You're right, 640 is okay, it is currently set at 750, but there doesn't seem to be any reason for that, it is really just a samba file server for windows clients.

---

### Post by Morbius1 on 2011-06-26
I re read my original post - It's late is my only excuse:

That command made no sense what so ever:

It should have been in two parts:
```
sudo chown root:users /path/to/shared/folder
```Followed by a chmod with a setgid:
```
sudo chmod 2770 /path/to/shared/folder
```

A thousand apologies.

---

### Post by Morbius1 on 2011-06-26
Ah, this is a Samba share - why didn't you say so :)

Just add the following lines in the share definition for that share:
```
force group = users

```Then restart samba.

When the remote user is allowed access every new file /folder will be set to group = users.
Other users will be recognized as having group = users so they will automatically have access to the file.

---

### Post by Kissell on 2011-06-26
Thanks, I guess that gets me there.  

I took a photo with my phone and it was automatically uploaded to the server through dropbox.  Dropbox is logged in as my user account, so even though the /Photos folder was set to "chown root:users", the new file inside that folder got the user and group equivalent of "chown myuser:myuser".  I can live with the default permissions of 644, but I really wanted the default user and group to be set to "root:users".  However, if the users across the samba share have read-only access to it, then I guess it doesn't matter what the linux group is set to.  It only bothers me because I'm OCDing over it, I guess there is no problem with the functionality with the change to the samba config.

---

### Post by capscrew on 2011-06-26
> **Kissell said:**
> Thanks, I guess that gets me there.  

I took a photo with my phone and it was automatically uploaded to the server through dropbox.  Dropbox is logged in as my user account, so even though the /Photos folder was set to "chown root:users", the new file inside that folder got the user and group equivalent of "chown myuser:myuser".  I can live with the default permissions of 644, but I really wanted the default user and group to be set to "root:users".  However, if the users across the samba share have read-only access to it, then I guess it doesn't matter what the linux group is set to.  It only bothers me because I'm OCDing over it, I guess there is no problem with the functionality with the change to the samba config.

It might be helpful if you revised your thoughts on file permissions (managed by chmod) and file ownership (chown and chgrp).  The initial mode ( in the kernel I believe) for directory permissions is 777 and for the directory is 666.  The UMASK variable is then used to set the default for for the system directories and files.  The umask of 022 sets this to 755 for directories and 644 for files.

There is no need for data files to have the execute bit set.  Why do you feel that you need 750 for these files.  Ignoring the setting of execute bit, both the owner and the group have read rights to the files in your example. The owner has read and write permissions.  My thoughts are: why does root have to explicitly have these rights declared by making root the owner of the file?  Root can do all of the manipulation without any assigned ownership or permission. 

Directories have different attributes.  As you can't "*execute *a directory" the execute bit is used for a different permission.  It allows the user or group to descend into (traverse) the directory.  A directory with 700 permissions allows the owner to read the directory contents and modify the name of the directory and manipulate the contents, including subdirectories.  If we change the mode (chmod) to 750 then the owner has all the same rights and the group has the right to view the files in that directory and open subdirectories.  Once again there is no advantage to having root as the owner.

You could revise your permissions on the directories and files on the system.  In particular the ones shared by samba.  I ended up changing the umask to 002.  This made the default for directories at 775 (rwx-rwx-r-x).  This is world readable and traversable by all. It is Read, write and traversable  by the owner and group you assign (and root by default of being...root).

The owner of a file should be the creator of the file and the rights will be read and write.  The group should contain the users that you want to be able to manipulate files (also read and write).  This can be set by the extended attributes mentioned by Morbius1.  These are the sticky bit (i.e. the ownership of the file cant change) and the setuid/setguid (i.e. on all files created).  For more details see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid")

I have my data files setup this way.  I allow the user to be determined by who created the file/directory and control who can use the file by the group membership.  The control is set so that the file stays owned by the original creator by setuid/setguid bits.  The sticky bit means that the creator is the only one who can delete the file (and root of course)  You could leave the umask at its default of 022 and then the group would only be able to read the file.

The creation mode of directories and files can be changed by Samba in the shares it controls with the "create" parameter.  You can read about it [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK").

I use the group *_smbusers_* for the users I allow access to the data in the shares.  Here is the root of my Samba shares located at /srv/share ```
drwxrwsr-t  8 capscrew smbusers 4096 2011-04-15 16:36 share
```

This is the public share at /srv/share/Public (anybody can add files)```
drwsrwsr-t 12 capscrew smbusers  4096 2011-06-19 09:22 Public
```

The share in Samba looks like this```
# Data Shared By All
[Public]
	comment = Public Share
	path = /srv/share/Public
	browseable = yes
	guest ok = yes
	writeable = yes
	create mask = 0775
	force create mode = 3775
	directory mask = 3775

```

I know this is long winded but I think it will give you ideas on how to setup your file system.  At the least it might provoke some questions.  As always YMMV.

---

### Post by Kissell on 2011-06-27
> **capscrew said:**
> 
There is no need for data files to have the execute bit set.  Why do you feel that you need 750 for these files. 

Actually, the reason the server has the permissions of 750 for most files and folders, is that it is a massive collection of data, and files are often moved into folders by users to be shared.  So lets say Bob creates a file, it will have the file permission will have bob as the owner and bob as the group.  Then when Bob moves the file to a shared folder, the other users can't use it, because they are not part of the bob group.  I have been solving this problem with a cron job.  I would like all the files to have a permission of 640 and be the group "users" or "smbusers" or whatever the shared group is...  the problem is if I do a "chmod 640 /path/to/share -R" then nobody can open any folders.  In order for a windows samba share to open a folder you must have the execute bit on the folder, that's why I've been using 750 instead of 640, because there is no way I'm going in there one at a time.  Unless there is a way to make chmod only apply to folders or only apply to files, then when I need to run a recursive chmod it needs to have the execute bit.  Without the execute bit the folders all say "access denied" when being accessed from windows across the network.

I think the "chmod g+s" or the samba config change has solved my problem, either one allows the group to be set to "users" so that the other users who aren't bob can use the file.  This relieves me from having to run a cron job all the freaking time to make the files usable.

---

