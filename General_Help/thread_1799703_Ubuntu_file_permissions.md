---
title: "Ubuntu file permissions"
date: 2011-07-08
forum: General Help
---

### Post by jcd29 on 2011-07-08
I have an external ext4 drive with 776 permissions.

- When I use it in another computer will the "owner" show up as the one in the computer in which the files were created?

- Will I be able to access and delete files?

- Would I be able to change the permissions from this new computer?

---

### Post by kanishkdudeja on 2011-07-08
Bump.

---

### Post by dasan on 2011-07-08
You can do all the thinks if you have root user privilege in the other computer and your drive is not protected

---

### Post by Morbius1 on 2011-07-08
>  - When I use it in another computer will the "owner" show up as the one in the computer in which the files were created?Yes
> - Will I be able to access and delete files?Only as root
>  - Would I be able to change the permissions from this new computer?    Only as root

Note: if your permissions are really 776 then the non root user won't even be able to see any content because of the last "6". Folders have to have the execute bit turned on so that the folder "can be opened" to view it's contents. Change it to 777.

At that point:
> - Will I be able to access and delete files?The new user will be able to add to and remove files from the drive but will not be able to edit any files - unless you made the files 666.

---

### Post by nomko on 2011-07-08
>  
[QUOTE]Will I be able to access and delete files?
Only as root
[/QUOTE]
Not really true. As a root you have full access to all files and folders. But as long as you as the user created a file or folder, you as user has full permission on that file or folder to delete/move/copy/etc. very file/folder created by you give you full permission over that file/folder which you created.

---

### Post by Morbius1 on 2011-07-08
> **nomko said:**
> Not really true. As a root you have full access to all files and folders. But as long as you as the user created a file or folder, you as user has full permission on that file or folder to delete/move/copy/etc. very file/folder created by you give you full permission over that file/folder which you created.
He's moving it to another computer. Different user. And as I stated above, with permissions of 776 the remote user will be "other" and won't see a darn thing on it.

---

### Post by diesch on 2011-07-08
There is no difference between an internal and an external drive. If you mount an external drive that contains a Linux file system it behaves and you can access it just like any other file system.

But note that the file system stores only UIDs, not user names:

Let's say you have two Linux boxes M1 and M2. Alice has UID 1000 on M1 and UID 1001 on M2, and Bob has UID 1001 on M1 and 1000 on M2.

Now you take a disk from M1 to M2 and mount it there. Then all files that belonged to Alice an M1 now belong to Bob on M2 (because he is that one that has UID 1000 here) and vice versa.

That only works for file systems which support Unix permissions. For other file systems, like NTFS or FAT, user and permission aren't stored on disk  but given as mount options.

---

### Post by Morbius1 on 2011-07-08
> **diesch said:**
> But note that the file system stores only UIDs, not user names:

Let's say you have two Linux boxes M1 and M2. Alice has UID 1000 on M1 and UID 1001 on M2, and Bob has UID 1001 on M1 and 1000 on M2.

Now you take a disk from M1 to M2 and mount it there. Then all files that belonged to Alice an M1 now belong to Bob on M2 (because he is that one that has UID 1000 here) and vice versa.
I had not considered that. I stand corrected. Of course there still might be a problem if the other Linux starts uid's at 500. Or if Alice never intended Bob to have write access to her files.

---

### Post by jcd29 on 2011-07-08
So I should just change all permissions to 777, and then in the new computer I'll be able to change the "owner" right?

---

### Post by diesch on 2011-07-08
Only root can change the owner, and the permissions doesn't matter. So you only need to change permission if you want to access the files with a different UID.

The user that is created on Ubuntu during the installation has always UID 1000 so if you are that user on both systems you don't need to change anything.

You can print the UID of your user using
```
 id -u
``` on the command line.

---

### Post by jcd29 on 2011-07-08
> **diesch said:**
> Only root can change the owner, and the permissions doesn't matter. So you only need to change permission if you want to access the files with a different UID.

The user that is created on Ubuntu during the installation has always UID 1000 so if you are that user on both systems you don't need to change anything.

You can print the UID of your user using
```
 id -u
``` on the command line.

Thanks! I just wanted to do it purely for vanity reasons. So that the disk's files and folders appear under my new username as owner.

---

