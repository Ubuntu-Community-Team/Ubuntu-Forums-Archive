---
title: "Samba Permissions Problem"
date: 2010-02-09
forum: General Help
---

### Post by johnsample on 2010-02-09
Hi all,

After what feels like weeks have tinkering around trying to get a Samba file server set up, I've finally given up!

I have 4 drives and 2 groups:

1) Dev - Available to all users in both groups (normal and admin)
2) Misc - Available to users in admin group only
3) Admin - Available to users in admin group only
4) Accounts - Available to users in admin group only

Drives 1 and 2 are working fine, with the correct access rights. 

Drives 3 and 4 can be browsed by admins only, but no changes can be made at all - files & directories can't be renamed/moved/deleted.

What is most confusing is that Drive 2 is set up exactly the same as Drives 3 and 4.


The process I went through to get them working:

1) Added the following to SMB.CONF:

```

[dev]
writable = yes
public = no
path = /media/files/dev
force group = normal
valid users = @normal
guest ok = no
create mode = 0664
directory mode = 0775

[misc]
writable = yes
public = no
path = /media/files/misc
guest ok = no
valid users = @admin
force group = admin
create mode = 0660
directory mode = 0770

[admin]
writable = yes
public = no
path = /media/files/admin
guest ok = no
valid users = @admin
force group = admin
create mode = 0660
directory mode = 0770

[accounts]
writable = yes
public = no
path = /media/files/accounts
guest ok = no
valid users = @admin
force group = admin
create mode = 0660
directory mode = 0770

```

2) Then used: *sudo find . type f/d - exec chmod XXX {} \; * to assign the same permissions (660/770 for admin only drives and 664/775 for normal drive) to all files and folders on the drives, changing parameters accordingly.

3) Finally, I used: *sudo chown root:normal /media/misc* to assign ownership to the Normal group on Drive 1.

And: *sudo chown root:admin /media/relevantfolder* to assign ownership to the Admin group on Drives 2, 3 and 4.


I have checked that all file permissions and ownership have been correctly assigned.

I have checked that the users trying to connect are definitely part of the admin group in Linux.

I have also tried assigning the group owner to a completely different group (sambashare).

If I try to assign the group owner to Normal on the admin drives, I then cannot even access the drive from within Ubuntu, despite being logged in as a user belonging to this group.


If anyone could shed any light on why I can't make any changes to files on drives 3 and 4, I'd be extremely grateful as there's absolutely nothing else I can think of to try now!

Cheers,
Steve

---

