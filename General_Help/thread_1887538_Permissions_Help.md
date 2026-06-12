---
title: "Permissions Help"
date: 2011-11-27
forum: General Help
---

### Post by simpic on 2011-11-27
Hi, 

Relative newbie here and I'm in the world of permissions trouble!

Background...

I'm migrating my SAB, SB & CP installs from my unRAID server to a new ubuntu server.
Everything is installed and running but it's having issues creating and moving files and folders.

unRAID Server: 

/mnt/cache is where I wish all the downloaded files to be stored
Owner & Group: nobody users 

ubuntu Server: 

Running SAB & SB as the only user I have setup called sp

I have added a user called sp to the unRAID box and added it to the users group.

grep users /etc/group
users:x:100:sp

The command id sp on the unRAID box gives me this...
id sp
uid=1003(sp) gid=98(nobody) groups=98(nobody),100(users)

The /mnt/cache folder is mounted on the ubuntu server as /mnt/cache

If I try and add a file to it on the ubuntu server I get the following... 
touch: cannot touch `test.test': Permission denied

Any ideas how I can make the user sp on the ubuntu server move and create files and folders on the unRAID server?

Thanks in advance

---

### Post by zia_7575 on 2011-11-27
put the sudo in the start of command..

---

### Post by simpic on 2011-11-27
Hi, 

Yep, it will work with sudo of course, but the apps can't use that so I need to figure out a way of letting them running as 'sp' to be able to write to the unRAID server.

---

