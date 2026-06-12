---
title: "same group permission for 2 different users in /home/folder1"
date: 2010-07-12
forum: General Help
---

### Post by AfrikaDietmar on 2010-07-12
Hello,

on the same laptop, i have created different users.

I allow 2 users to share files among themsleves in a folder that i set in:
sudo mkdir /home/folder1

User1 and User2 can put files in there, and when User1 is logged in he can see which files User2 left him and vice versa. (No networking).

I've created a group1 where I added User1 and User2.
With System > Administration > Users and Groups under advanced i set both users "Main Group" on group1.

The folder1 in home, i did the following:
sudo chmod 774 -R /home/folder1
sudo chown -R User1:group1 /home/folder1


When User1 saves a file or copies a file from his home folder i.e.  /home/User1 into folder 1 in home/folder1 and when i chek the files  permission it says under group permission Read only.

When User2 saves a file or copies a file from his home folder i.e. /home/User2 into folder 1 in home/folder1 and when i chek the files permission it says under group permission Read only.

Is there a way to solve this that when User1 and User2 saves something in folder 1, it also gets the group permission Read & Write ? (Without having to set it each time with the pulldown menu under properties > permissions.)

---

### Post by geirha on 2010-07-12
With access control lists you can. [http://acl.bestbits.at/about.html](http://acl.bestbits.at/about.html)

Or you can do it quick and dirty by running chmod from cron every X minutes. That's not the best solution though. :)

Btw, you probably wanted chmod 2775 on that dir...

---

### Post by sisco311 on 2010-07-12
[thread=1460472]HowTo: Create a shared directory for local users (with bindfs).[/thread]

---

### Post by AfrikaDietmar on 2010-07-12
hi, i've installed acl and eiciel but the graphical functionality won't show when i click on properties, i don't get to see the acl functions through eiciel.

I did the chmod again with the 2775.

My current solution is that i have included a text file with the chmod function, so the user just copy and paste it in its terminal and gains his group rights each time..., but thats not so neat in case i want to give some restrictions.

Cron job could be another way to do this less often.

But the best would be, when User1 and User2 save something in folder1 the group permission is set on Read & Write instead of Read only...

Since i cannot solve this by clicking under permissions on acl through eiciel, do you know of any other way ?

---

### Post by AfrikaDietmar on 2010-07-12
Ok, i'll have a look at bindfs.

---

### Post by vanadium on 2010-07-12
To handle this with the standard permission system, you should also change the umask. This defines the default permissions for new files. By default, it is 755 or 644, where you want 775 or 644.

You can change that at the system level in the file /etc/profile, or per user in .profile.

---

### Post by AfrikaDietmar on 2010-07-12
Hi vanadium,

concerning the /etc/profile that was a good hint. But if i change the umask in the profile it seems to conflict with **/etc/pam.d/common-session **i.e. when i type in the terminal umask i will get 022 or 0022 if i added a zero.

Instead i put a "#" in front of the umask in gksu gedit /etc/profile

And then opened gksu gedit [B]/etc/pam.d/common-session
[/B]There I added: [COLOR=Red]session    optional     pam_umask.so umask=002


[COLOR=Black]This page was helpful for understanding better umask: [http://linuxzoo.net/page/sec_umask.html](http://linuxzoo.net/page/sec_umask.html)

When User1 and User2 create files these are for the owner and group now readable and writable. I'll need to chmod all the old files. 

Just wondering, is it also possible for example when moving a file that has group read only into folder1 which is shared to change group into read & write ? 
[/COLOR][/COLOR][COLOR=Red][COLOR=Black]
[/COLOR]
[/COLOR]

---

### Post by vanadium on 2010-07-13
Thank you for this valuable feedback, which is very useful for me.

> Just wondering, is it also possible for example when moving a file that has group read only into folder1 which is shared to change group into read & write ? 
I don't believe this is possible with the standard permission system. For this, you need a more granular system like "access control lists" (acl). I have no experience with this.

---

### Post by AfrikaDietmar on 2010-07-13
Hi vanadium, you're welcome.

Ok, but somehow acl/eiciel is not working properly for me in 10.04. It used to before, but somehow with all the clicking and trying i never really got to the required results where in the end it was just better to use the terminal and chmod and so on.

> Quote:
 	 	 		 			 				Just wondering, is it also possible for example when moving a file  that has group read only into folder1 which is shared to change group  into read & write ? 			 		

I actually achieve this in another way with Samba.
In the smb.conf file i use force user function to achieve it.

For example if i use the pc which is the file server, i click myself through the network, input the samba users login and password, and then save a file, even if it has read permissions for group only, there it gets changed. But on that same PC, if i don't navigate through the network and just access the folders directly in /home/ i then don't have this effect.

But for this thread, theme and issue, i was wondering if there is another work around for a folder that will not be used in a network anyway, i won't setup samba just for this. The umask was the fix in this case.

---

### Post by vanadium on 2010-07-13
"Group read only" cannot automatically be converted to group read/write. It remains a matter of changing the permissions manually, or having appropriate default permissions set using umask.

Concerning your initial question, I bumped into this interesting read: [http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm)

With the "Sticky bit on Directories", the group of the directory is automatically assigned to any file that is created in the directory. Thus, any file that is created there will be assigned that group. Both users will be granted the group permissions if they are member the group.

In the same link, you will find how acls allow to have a "per directory" umask. However, it requires installing and using that different permission system. It may not be worth the trouble for you.

---

### Post by sisco311 on 2010-07-13
> **AfrikaDietmar said:**
> 
I actually achieve this in another way with Samba.
In the smb.conf file i use force user function to achieve it.


bindfs works in a similar way. It allows you to remount (bind) a file/directory with different permissions, e.g.:
```
sudo bindfs -o perms=0700,mirror=user1:user2 path/to/dir path/to/dir
```

user1 & user2 will see themselves as the owner of the dir and they will have read/write/execute access for all the directories and subdirectories and read/write access for all the files from dir.

---

### Post by geirha on 2010-07-13
Note that for acls to work, the filesystem must be mounted with the acl option.

So add the acl option to the relevant filesystem in /etc/fstab
```
UUID=...  /home ext4 relatime[color=red],acl[/color] 0 2
```
Then reboot or remount it. 
```
sudo mount -o remount /home
```

---

