---
title: "mounting on a network"
date: 2011-03-11
forum: General Help
---

### Post by UglieFrog on 2011-03-11
How do i mount these they are in a separate computer


MythTV Drive #1:
Directories: myth-box:/var/lib/mythtv/livetv, myth-box:/var/lib/mythtv/recordings

---

### Post by markeee on 2011-03-11
there's two ways that spring to mind, either using NFS or Samba
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

have a look at the above, think it covers what you're trying to do!

---

### Post by UglieFrog on 2011-03-11
I followed this guide which is very confusing 
[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

i get this error

there has to be a better guide somwhere


mount.nfs: access denied by server while mounting xxx.xxx.x.xxx:/var/lib/mythtv/recordings

---

### Post by PoHandle on 2011-03-11
Could you please paste the contents of your */etc/exports* file?

You can type```
cat /etc/exports
```in a terminal.

---

### Post by UglieFrog on 2011-03-11
/var/lib/mythtv/recordings  192.168.1.125(rw,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos      192.168.1.125(rw,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music       192.168.1.125(rw,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    192.168.1.125(rw,async,no_root_squash,no_subtree_check)

---

### Post by markeee on 2011-03-11
what are you trying to do mount the nfs share on a client machine?!

---

### Post by UglieFrog on 2011-03-11
yes...thats from the server machine...i call it box a....I want to communicate with box a using box b

---

