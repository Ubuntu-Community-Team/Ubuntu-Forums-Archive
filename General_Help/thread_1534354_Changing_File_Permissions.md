---
title: "Changing File Permissions"
date: 2010-07-19
forum: General Help
---

### Post by mondomunchies on 2010-07-19
I have an external harddrive.  I couldn't change any permissions so I found out how to 

sudo umount /dev/sdb1
sudo mount -o uid=myusername,gid=myusername -t ntfs-3g /dev/sdb1 /media/LaCie

That worked fine.  When I go into the folders on the drive and go to Properties>Permissions, I see 

Owner: myusername
Folder Access: Create and delete
File access: ---

Group: myusername
Folder access: create & delete
File access: ---

Others
Folder access: create & delete
File access: ---

Every time I try to click on the file access and change it, it stays for a second then switches back, if I close the window real fast and open it again its changed anyway. I tried using 

sudo chmod 777 -R /myfolder

I know this isnt great for security but I'm so irritated at this point I would invite hackers to break my s*** so I wouldnt have to deal with it anymore.

So I can only change folder access by using special mounting commands and I have no control over file access

I would prefer
Folder access drwx-rx-rx
File access -rwx-rx-rx

I'm not even sure if thats how you write out the long version of permissions.

I'm stressed out.  Any ideas?

---

### Post by dino99 on 2010-07-19
into synaptic you can install an easy tool to deal with partitions and devices rights: mountmanager

then set your prefs with it: system admin mountmanager

---

### Post by jv2112 on 2010-07-19
sudo chmod 755 -R /myfolder (what you asked for) or even better sudo chmod 700 -R /

If you are the owner and you only want you to have access the second option is better.

---

### Post by sisco311 on 2010-07-19
> **mondomunchies said:**
> 

I would prefer
Folder access drwx-rx-rx
File access -rwx-rx-rx

I'm not even sure if thats how you write out the long version of permissions.

I'm stressed out.  Any ideas?

You can set the permissions with the umask, fmask and dmask mount options:
```
sudo mount -o uid=myusername,gid=myusername,umask=022 ...
```

umask - sets  the  umask  (the  bitmask  of  the permissions that are not present);
dmask - sets the umask applied to directories only and
fmask - sets the umask applied to regular files only.

---

