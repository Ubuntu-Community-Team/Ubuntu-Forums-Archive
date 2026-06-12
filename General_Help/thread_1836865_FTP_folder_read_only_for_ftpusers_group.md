---
title: "FTP folder read only for ftpusers group"
date: 2011-08-31
forum: General Help
---

### Post by berryboy on 2011-08-31
hello,
hopefully the title was clear :)

im using vsftpd with local users, i download stuff with deluge into the ftp folder, then users logged in through vsftpd as local users have that ftp folder mounted into their home directory's so they can download, i ahve tried 

chown -R deluge:ftpusers /home/ftp
chmod -R 744 /home/ftp 

so it should now be read only for the group ftpusers, however when i log in to a account i can not browse/download the content, if i change it too 

chmod -R 774 /home/ftp

it works fine :/

i just want local users to have read/download only permissions on that directory.

any help would be great :)

---

### Post by berryboy on 2011-09-01
bumping for help :'(

---

### Post by berryboy on 2011-09-02
please someone help :/
 

would it be that im mounting a folder that is out side the users home folder of which they are chrooted too ? im really stuck here :/

---

### Post by berryboy on 2011-09-04
unfortunately i have still been unable to find a solution for this, maybe this forum is not the best place for this type of thing. could someone recommend a place i could try i only really know this place, which has been most helpful in the passed

---

