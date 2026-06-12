---
title: "user and group permissions"
date: 2011-01-08
forum: General Help
---

### Post by watgrad on 2011-01-08
Can anyone point me to a good explanation of the user and group permissions settings?  I'm relatively new to Ubuntu, and would like to better understand how this works.

I have done some of the online manual reading (like the community documentation and 'Ubuntu Unleashed' - but these resources seem to gloss over how this works (maybe they assume people are familiar with the concept?).

Anyway, I thought that if I created a new group like 'Shared_files', then create a folder and added it to the group, then I could give certain user accounts access to the folder (and it's contents) by adding the 'Shared_files' group to each user account.  Sadly this didn't work for me, so I must not understand...

Is there a comprehensive explanation of this anywhere that someone could point me toward?

Thanks,
John

---

### Post by AlphaLexman on 2011-01-08
Take a look [here.]("http://www.freeos.com/articles/3127/")

---

### Post by efflandt on 2011-01-08
You not only need to know about users and groups, but also need to study **directory and file permissions**.

There are different **group** permissions you can give to a directory depending upon whether you want anyone in the group to be able to create/modify/delete directories and files under that which inherit that special group, or whether they inherit the group of the user and it is up to the user to set group and group permissions for files they want others in the group to be able to modify or delete.  **man chmod** gives some basics, but you may need to experiment with the **s** bit for group or **t** bit for directory owner with 2 different users in the group to see if things work the way you expect.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by sisco311 on 2011-01-08
> **watgrad said:**
> 
Is there a comprehensive explanation of this anywhere that someone could point me toward?


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
and/or
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by watgrad on 2011-01-08
[http://ubuntuforums.org/showthread.php?t=350067](http://ubuntuforums.org/showthread.php?t=350067)

Thanks all for your help - above post was also useful for me.

---

