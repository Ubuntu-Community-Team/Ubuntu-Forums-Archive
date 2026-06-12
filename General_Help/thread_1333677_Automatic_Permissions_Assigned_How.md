---
title: "Automatic Permissions Assigned? How?"
date: 2009-11-21
forum: General Help
---

### Post by Roasted on 2009-11-21
I have a directory on my system where a hard drive mounts to. That directory is shared.

I would like ANY and ALL files/folders that are created from ANY of these users to come down with permissions of 775.

How can I do this? (preferably without umask as that doesn't seem to look like a valid alternative)

---

### Post by sisco311 on 2009-11-21
[https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport]("https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport")

[http://www.youtube.com/watch?v=6piQXXHTmqk]("http://www.youtube.com/watch?v=6piQXXHTmqk")

---

### Post by sisco311 on 2009-11-21
okay, i think i figured it out :)

that youtube wideo is awesome 


[list]
[*] install acl:
```
sudo apt-get install acl
```

[*] edit the fstab and add acl to the mount options

[*] remount the partition:
```
sudo mount -o remount /mount/point
```

[*] create a new group:
```
sudo addgroup shared
```

[*] add the users to the group:
```
sudo adduser username shared
```
NOTE: you may have to log out the user and log it back in.

[*] set the acl permissions:
```
sudo setfacl -Rdm g:shared:rwx /mount/point
sudo setfacl -Rm g:shared:rwx /mount/point
```

[*] done. users in the shared group now can read/write/execute files in /mount/point
(even if the share is owned by root:root with 0700 permissions! the linux permissions do not matter at all :) )

[/list]

If you need a GUI to edit ACLs install [eiciel]("apt://eiciel") (apturl link). It integrates in nautilus (right click -> Properties -> Access Control List).

---

### Post by Roasted on 2009-11-21
One thing I noticed in the video I saw on YouTube was the guy mentioned the directory in question he was owned by root:root with 700 permissions, so no other users had access to that folder. Is that the way to set the permissions up? Should my Linux permissions on the folder be 700 with root:root ownership and let the ACLs handle the rest? Is that even possible?

Secondly, within /media/storage I have more shares in there. Should I set an ACL to each directory within storage? Or should I just set one massive ACL to storage? 

I'm using a GUI program known as Eiciel to handle this. Is there any way I can add other ACL lists with each share in question to customize each shares permissions?

---

### Post by sisco311 on 2009-11-21
> **Roasted said:**
> One thing I noticed in the video I saw on YouTube was the guy mentioned the directory in question he was owned by root:root with 700 permissions, so no other users had access to that folder. Is that the way to set the permissions up? Should my Linux permissions on the folder be 700 with root:root ownership and let the ACLs handle the rest? Is that even possible?


Only the acl ownership and permissions count. By default, the acl permissions and ownership are the same as the unix/linux permissions/ownership.
  

> **Roasted said:**
> 
Secondly, within /media/storage I have more shares in there. Should I set an ACL to each directory within storage? Or should I just set one massive ACL to storage? 


*setfacl -R* sets the permissions recursively, so it will apply to sub directories as well.  

> **Roasted said:**
> 
I'm using a GUI program known as Eiciel to handle this. Is there any way I can add other ACL lists with each share in question to customize each shares permissions?

Sorry, I don't think I don't understand this. 

If you are the owner of the file/folder, then you can customize the permissions.

---

### Post by Roasted on 2009-11-21
> **sisco311 said:**
> Only the acl ownership and permissions count. By default, the acl permissions and ownership are the same as the unix/linux permissions/ownership.


I don't get this. How did he apply 700 perms with root:root. Do ACLs take primary?

> 
*setfacl -R* sets the permissions recursively, so it will apply to sub directories as well.  


So if I run sudofacl -R to /media/storage, would ANY file written in that directory whether it be through the network via Samba OR locally on the machine, will the data come through with the ACL perms at that point?

> 
Sorry, I don't think I don't understand this. 

If you are the owner of the file/folder, then you can customize the permissions.

Right, but I want to be able to drop a file in storage as jason and the permissions come down as 775, but by default they come down as 755. I need group to have "7" permissions. Will ACLs auto-apply permissions like this? Or will they simply control individualized user access? That's truly what I need, is a method to know that when I drop a file in storage - BAM - it gets 775 perms automatically, or 777, or 750, or whatever perms I decide that's what I need, but only on a directory basis, such as my situation with /media/storage. Will it handle this?

---

