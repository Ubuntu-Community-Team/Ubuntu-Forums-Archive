---
title: "Owner/group rights confusion."
date: 2010-09-08
forum: General Help
---

### Post by Coder68 on 2010-09-08
Does Ubuntu do something a little different with these rights? It would seem that the owner if a file, with no permissions at all, can still change the permissions on the file.

From all my Googleing around, it appears that only the owner of the file or root can change the permissions of a file. So, I took a file that I owned and removed all permissions for the owner, but left them for the group users. 

[PHP]----rwx--- 1 coder68 users 30140 2008-06-23 04:02 file[/PHP]I am not a member of users, but I was still able to run chmod to 770 as myself. (no sudo) Is this because as the owner, I can't lock myself out? Is this a Linux thing or an Ubuntu thing?



If a member of the group users has full acces to the file, can they change the permissions? If so, what is the minimum access they need to do this.  I can't seem to test this correctly.

Thanks,

C68

---

### Post by Rubi1200 on 2010-09-08
Great question!

I  don't have answers for all your points, but I hope this helps clarify certain things:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Coder68 on 2010-09-08
Yeah, I read that.  Along with several dozen other explanations. Since I do not run ACL's I thought file permissions were the ONLY source of control for files.  No permissions = no access period. But this is not true, at least not in Ubuntu 8.10.

Hopefully someone will have a direct answer soon, as this is one of the questions in my class book. And no, the book does not even mention this area of info, but it does ask it.  Very bad book. 

Thanks,

C68

---

### Post by endotherm on 2010-09-08
yes the only check to determine if you can chmod is the ownership. you do not need RW or x access to do it. that is because permissions are stored in the "inode" that points to a file, not in the file itself, so you don;t actually write to the file to make the change. 
yes it;s a safety consideration, to make sure that you can't lock yourself out on accident, or lock the admin out.

I don't believe that a group member that does not own an object can modify it's permissions. the existance of the sticky bit kind of implies otherwise, but, try it out just to confirm. 

[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html)

---

