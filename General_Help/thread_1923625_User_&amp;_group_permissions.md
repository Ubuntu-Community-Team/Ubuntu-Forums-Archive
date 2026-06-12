---
title: "User &amp; group permissions"
date: 2012-02-11
forum: General Help
---

### Post by twfry on 2012-02-11
Hello,
 
I've run Ubuntu as a family file server for awhile, and now want to add real permission rules between people, but can not figure out how to effectively do so. 
 
If anyone knows how to setup the file user, group and other permissions (i.e. the combination of -rwxrwxrwx) to handle the situation below, please let me know. I've tried for awhile now and can't figure it out.
 
Below is an example of what I am trying to do:
 
User accounts are: a) Dad, b) Mom, c) Kid1, d) Kid2
 
Folders and access permissions are:
a) DadFiles - read/write Dad only
b) MomFiles - read/write Mom only
c) ParentFiles - read/write Dad & Mom
d) Kid1Files - read/write Kid1, Dad & Mom
e) Kid2Files - read/write Kid2, Dad & Mom
f) FamilyFiles - read/write All
 
Any suggestions?
 
Thanks,

---

### Post by TitanusEramius on 2012-02-11
I'll guess you have to use a combination of users and groups to archive what you need, file permissions in itself is not enough.

If you where to create the user "kid", then a group with the same name is created and the user "kid" is automatically made a member of it. If you then add "dad" to the group "kid" and assigns 775 = rwxrwxr-x to kids files, then you are golden :)

However, you have to ensure "kid"s files always are created with 775 so "dad" also have ownership, otherwise, if created with 755 = rwxr-xr-x then will "dad" only be able to see "kid"s files, not edit or delete them. I don't know how to insure this, I guess a sticky bit on the folder could do it, but you have to look that up.

For "family" it's pretty much the same, that user just needs to be part of all the other groups.

Good luck

---

### Post by savanna on 2012-02-11
For more complicated permission requirements like these, you can use ACL's (Access Control Lists).

Eg checkout [http://www.suse.de/~agruen/acl/linux-acls/online/](http://www.suse.de/~agruen/acl/linux-acls/online/)

---

### Post by Lars Noodén on 2012-02-11
Here's a guess.  You'll want to walk through it on paper first to be sure.

```

# DadFiles - read/write Dad only
sudo chmod u=rwx,g=,o= /home/dad/


# MomFiles - read/write Mom only
sudo chmod u=rwx,g=,o= /home/mom/


# ParentFiles - read/write Dad & Mom
sudo mkdir /home/parents
sudo addgroup parents

sudo gpasswd --add dad parents
sudo gpasswd --add mom parents

sudo chgrp -R parents /home/parents
sudo find /home/parents -type d -exec chmod g=rwxs "{}" \;
sudo find /home/parents -type f -exec chmod g=rws  "{}" \;


# Kid1Files - read/write Kid1, Dad & Mom
sudo gpasswd --add dad kid1
sudo gpasswd --add mom kid1

sudo chgrp -R kid1 /home/kid1
sudo find /home/kid1 -type d -exec chmod g=rwxs "{}" \;
sudo find /home/kid1 -type f -exec chmod g=rws  "{}" \;


# Kid2Files - read/write Kid2, Dad & Mom
sudo gpasswd --add dad kid2
sudo gpasswd --add mom kid2

sudo chgrp -R kid2 /home/kid2
sudo find /home/kid2 -type d -exec chmod g=rwxs "{}" \;
sudo find /home/kid2 -type f -exec chmod g=rws  "{}" \;


# FamilyFiles - read/write All
sudo mkdir /home/family
sudo addgroup family

sudo gpasswd --add dad family
sudo gpasswd --add mom family
sudo gpasswd --add kid1 family
sudo gpasswd --add kid2 family

sudo chgrp -R family /home/family
sudo find /home/family -type d -exec chmod g=rwxs "{}" \;
sudo find /home/family -type f -exec chmod g=rws  "{}" \;


```

---

### Post by twfry on 2012-02-11
Thanks for the help everyone. 
 
Lars I believe your solution focused on adding groups should work. Thanks a lot for the detailed steps. 
 
It was the 's' permision on the directories that I did not understand before and after reading how that works I think that should do it. The reason I didn't think to try using groups that way was due to how new files are created, but it seems this will take care of that. 
 
The one drawback seems to be what happens when the kids become old enough to figure out how to do a chmod g-a command. That's still pretty far out though. :o

---

