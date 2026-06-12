---
title: "Ubuntu nt acl support not working"
date: 2009-07-09
forum: General Help
---

### Post by gbhardin on 2009-07-09
New ubuntu user and need assistance with permissions using the 
nt acl support = Yes line in samba.conf. The configuration for the share is as follows
[GH]
comment = <my dir>
browseable = yes
guest ok = no
read only = no
path = /srv/samba/<my dir>
create mask = 0660
directory mask = 0770
admin users = @"<mydomain>\Domain Admins"
valid users = @"<my domain>", @"<my domain>\<specific user group>"
nt acl support = Yes
 
When I try to modify the folder permissions of specific user group, it replicates the user group in the advanced security window with new permissions that I've just set up.
I've also created a single AD user and placed in a AD group and cannot get the properties of the group to apply to the folder or file level. The only way I can see changes in file permissions is when I change my mask's. It seems as thought the nt acl support exist, but is not effective in directory.
 
Desired permissions:
 
On existing folders, subfolder and files I would like all users within a group to be 
able to read, write, create folders, DO NOT want ability to DELETE.

---

### Post by neuropierre on 2011-10-08
> **gbhardin said:**
> New ubuntu user and need assistance with permissions using the 
nt acl support = Yes line in samba.conf. The configuration for the share is as follows
[GH]
comment = <my dir>
browseable = yes
guest ok = no
read only = no
path = /srv/samba/<my dir>
create mask = 0660
directory mask = 0770
admin users = @"<mydomain>\Domain Admins"
valid users = @"<my domain>", @"<my domain>\<specific user group>"
nt acl support = Yes
 
When I try to modify the folder permissions of specific user group, it replicates the user group in the advanced security window with new permissions that I've just set up.
I've also created a single AD user and placed in a AD group and cannot get the properties of the group to apply to the folder or file level. The only way I can see changes in file permissions is when I change my mask's. It seems as thought the nt acl support exist, but is not effective in directory.
 
Desired permissions:
 
On existing folders, subfolder and files I would like all users within a group to be 
able to read, write, create folders, DO NOT want ability to DELETE.

I´m having the same problem. I get an error from windows when triyng to modify permissions....

---

