---
title: "Owner and Group permissions on filesystems accessed by multiple Ubuntu OSes"
date: 2009-08-06
forum: General Help
---

### Post by Mka on 2009-08-06
I have 4 linux sytems on one machine (3 ubuntu and 1 debian lenny) and decided having a separate small ext3 partition for MySQL database shared among them. I did this migration successfully on the first OS. 

Then I had to update the /etc/fstab and files in /etc/mysql and /etc/apparmor.d accordingly on another OSes. When I restart the mysql daemon it cries about permissions. So I went to the new MySQL filesystem and did a ls -l and found out the files that where supposed to be owned the user "mysql" and group "mysql" are owned by another user (on one system it's "mt-daapd" on another one it's "vdr"). 

I tried fiddling with "chown" but to no luck. Is it possible to synchronise the /etc/group and its allies so that the id of the user is the same for all the OSes (mysql has id 117 on one OS, then 113 on another one and so on)?

---

