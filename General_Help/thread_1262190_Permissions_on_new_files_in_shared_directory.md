---
title: "Permissions on new files in shared directory"
date: 2009-09-09
forum: General Help
---

### Post by deepthink on 2009-09-09
I have a directory that is supposed to be shared between users that belong to the share-photos group. The directory has the setgid-bit set and all directories and files that are created do get the same group.

What I have not been able to solve is that I want new directories to have -rwxrwx--- and files to have -rw-rw---- but only for the shared photos directory. For other files I would like to leave the default. What would be the best way to accomplish this. I cant expect my users to run umask nor to manually set the permissions after copying new photos.

Thanks

---

### Post by deepthink on 2009-09-13
Is this not possible? Am I the only one with this particular request or have I misunderstood the permission system?

---

### Post by StuartN on 2009-09-13
> **deepthink said:**
> I want new directories to have -rwxrwx--- and files to have -rw-rw----

Is that not what happens at the moment, assuming your users have the default umask of 022?

---

### Post by deepthink on 2009-09-13
No, the following happens:
```
alexander@server:~$ touch test
alexander@server:~$ ls -lh test
-rw-r--r-- 1 alexander alexander 0 2009-09-13 14:36 test
alexander@server:~$ umask
0022
```Where should I change the umask so it affects all users? I guess I need to set it to 0007. 
```
alexander@server:~$ umask 0007
alexander@server:~$ touch test
alexander@server:~$ ls -lh test
-rw-rw---- 1 alexander alexander 0 2009-09-13 14:39 test

```Will that have any other implications? Like files created system users that will no longer be world readable which in turn will brake stuff?

Is it not possible to tie a umask too a particular directory?

---

### Post by StuartN on 2009-09-13
> **deepthink said:**
> Will that have any other implications? Like files created system users that will no longer be world readable which in turn will brake stuff?Is it not possible to tie a umask too a particular directory?

It is a bad idea in general to make all files writeable by others, so setting umask to 0007 or 0002 would mean you have to trust all other users, who will have write access to all your files. No, you cannot umask a particular directory. The normal group read-only permissions don't break things, and super-user can change permissions if files do get locked.

Can't individuals chmod g+w their shared files before loading them into the shared directory?

---

### Post by deepthink on 2009-09-13
This was way more complicated than I expected it to be. But there seem to be allot in the works... 

[https://wiki.ubuntu.com/MultiUserManagement](https://wiki.ubuntu.com/MultiUserManagement)

Bindfs might be viable but seems to be a bit overkill
[http://manpages.ubuntu.com/manpages/intrepid/man1/bindfs.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/bindfs.1.html)

A umask of 007 will not make files writable to all. Only to members of the same primary group were each user has their own group. 

I can't expect my family to set the permissions. They will just think it is not working when they can't access the files.

---

### Post by bodhi.zazen on 2009-09-13
You would think it would be easier to share directories, but alas.

IMO acl are best :

Share directory : [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)
    Set Group ID : chmod g+s dirname

    OR (ACL works better)

    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)

---

### Post by XxionxX on 2009-09-13
This toutorial really helped me out with file permissions. [http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html). I hope that helps.

---

