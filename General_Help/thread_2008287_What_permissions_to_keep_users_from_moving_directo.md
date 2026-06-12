---
title: "What permissions to keep users from moving directories?"
date: 2012-06-22
forum: General Help
---

### Post by lisanels47 on 2012-06-22
I understand the permissions for the most part, but how can I set them so a user can read the contents of the directory, but not move the directory?  Example:

/data/office/myfile.txt

I want them to be able to read and write myfile.txt, but not move the office directory anywhere.  

And would they still be able to create a link to their desktop?  I've had a couple people move the directory to their desktop and everyone else freaks out.

Thanks,
Lisa

---

### Post by dino99 on 2012-06-22
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

chown let you set the owner, so if your user(s) dont earn these files/folders, that means that you (the admin) have only the rights.

---

### Post by lisanels47 on 2012-06-22
Yes, I'm aware of that, what I'm looking for is a way to keep users that have read/write access to the 'office' directory to not have the permissions to move or delete that directory.

---

### Post by sisco311 on 2012-06-22
If they have write and execute access to /data **!!!**, then they are allowed to delete or move the files/directories from /data. Please check out the directory permissions section @ [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by sisco311 on 2012-06-22
> **dino99 said:**
> [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

chown let you set the owner, so if your user(s) dont earn these files/folders, that means that you (the admin) have only the rights.

That's not true. If the sticky bit is not set on the directory, then any user with write permission to the directory ( and execute permission to all its ancestors ) can delete files/directories from it regardless of the owner of the files/directories.

```
[sisco@acme xtmp]$ mkdir foo-owned-by-sisco
[sisco@acme xtmp]$ sudo mkdir foo-owned-by-sisco/bar-owned-by-root
[sisco@acme xtmp]$ ls -all foo-owned-by-sisco/
total 200
drwxr-xr-x 3 sisco users   4096 Jun 22 18:19 .
drwxr-xr-x 3 sisco users 192512 Jun 22 18:19 ..
drwxr-xr-x 2 **root  root**    4096 Jun 22 18:19 bar-owned-by-root
[sisco@acme xtmp]$ rmdir foo-owned-by-sisco/bar-owned-by-**root**/
[sisco@acme xtmp]$ ls -al foo-owned-by-sisco/
total 196
drwxr-xr-x 2 sisco users   4096 Jun 22 18:19 .
drwxr-xr-x 3 sisco users 192512 Jun 22 18:19 ..

```

---

### Post by lisanels47 on 2012-06-22
/data/office/myfile.txt

So If I change /data to have READ/Execute permissions, could users still move/delete the office directory?  

so:
755 /data
777 /data/office
666 /data/office/myfile.txt

?

---

