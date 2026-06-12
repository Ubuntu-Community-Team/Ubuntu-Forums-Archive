---
title: "Deny delete"
date: 2010-07-08
forum: General Help
---

### Post by Edhas on 2010-07-08
Hi All,

  I was wondering that with "chmod" I can successfully block access to files. But if I delete the file it just asks a qs that if I'm sure to delete the read-only file before deleting. Suppose when a file is being created as "root" (by sudo su) it should not get deleted either by me or any other user. Only root should be able to delete it. Now the qs is how to disable the rm/cp/mv options either from gui or cli for such restricted files. I'm new to ubuntu and in general linux commands. 

Thanks in advance to all of you.

---

### Post by sisco311 on 2010-07-08
Hi and welcome to the forums!

Please check out:
[http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm)

*To modify the contents of a directory requires write permission.  If you have write permission on some directory, you can add files to it, rename and delete files from it. Deleting, linking, and renaming files require execute permission too.*

---

### Post by 3rdalbum on 2010-07-08
There's two ways. 

1. Remove write support for everyone except the owner, and make the owner root. This is best done using the "Advanced Permissions" editor in Nautilus. If you open gconf-editor as root:

```
gksudo gconf-editor
```

It's under /apps/nautilus and check "Show advanced permissions".

Now run Nautilus as root:

```
gksudo nautilus
```

Navigate to the file whose permissions you want to modify, and right-click it. Go to Properties and then the Permissions tab.

Change the owner and group to "root" and then remove write permission from "Others". Now only root can delete the file.

(in the event that sisco is right and that deleting is a function of the enclosing directory rather than the file: Then you'd do this to the directory, not to the file)

2. Little-known method:

You can use chattr +i <filename> to make the file unremovable, even by root. I have heard that this only works on Ext2(/3/4) and XFS filesystems, but you're extremely likely to be using an Ext filesystem anyway. You can use "chattr -i <filename>" to remove the lock and make the file removable again.

Note that this will actually make the file immutable; so you can't even modify it unless you remove the lock.

Use this method in front of other Unix/Linux users in order to make them gasp and think that you're really l33t :-P

---

### Post by Edhas on 2010-07-08
Thank you for your reply. I figured out that the owner should be root as u mentioned and the issue will be resolved. I used the following combination..

user# sudo su
root# chown root test
root# chmod -rwx-- test
exit

And the issue was resoled. the idea was to change the owner. Thank you again for the reply.

---

