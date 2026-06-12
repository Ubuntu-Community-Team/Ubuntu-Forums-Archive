---
title: "Stick Bit Doubt?"
date: 2009-10-26
forum: General Help
---

### Post by sahabcse on 2009-10-26
Hi All

I have created one file and set the permission 1775 (sticky bit), then I have login by another user and try to write to that file but it showing read only file.


Definition:sticky bit is a special permission by which a user or all users can get write privilege to a file but can not delete it. only the owner of the file can delete"

More Info
---------
-rwxrwxr-t 1 ubuntu ubuntu   10 2009-10-26 15:28 test ---> sticky bit     
                                                           permission file

id sahab
uid=1000(sahab) gid=1000(sahab) groups=1000(sahab),1001(ubuntu)

I have tried to write from username sahab. But I can't able to write also ubuntu is the secondary group of sahab. Kindly help me regarding this issue.

---

### Post by phillw on 2009-10-26
Hi,

there's a thread on chmod just been active ...

[http://ubuntuforums.org/showthread.php?t=1299346&highlight=chmod](http://ubuntuforums.org/showthread.php?t=1299346&highlight=chmod)

It should answer your questions & give you resources to read up on it.

Regards,

Phill.

---

### Post by sahabcse on 2009-10-26
thanks for fast response, I have tried the command g+w filename, still showing same error, screen shots attached here for more info

---

### Post by phillw on 2009-10-26
[http://www.webmasterworld.com/forum40/113.htm](http://www.webmasterworld.com/forum40/113.htm)

I think may describe it better for you.

setting the sticky bit of 1 is used for directories to achieve what you want, well, I *think* that's what you're trying to achieve. Anyways, that thread does a decent job of describing the use of stickbits (a bit further down the page, after the intro into chmod)


> [FONT=verdana][SIZE=2][COLOR=#000000]By default, if you own the directory or have the proper permissions, you have the authority to remove files from it. This is done at the directory level instead of the file level because when you create or remove a file, you are adding or removing an entry in the directory (think of it as altering the contents of the directory). [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]This creates a problem with scratch areas that all users can toss files in, such as /tmp. User "joe" could put a file in /tmp and user "jane" could delete it (because jane has rwx access to the directory). [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]The sticky-bit on directories forces the behavior that (within that directory with the sticky-bit set) **only** the **owner** of the file can remove the file. The same applies to directories within that directory that has the sticky-bit set. To continue the above example, joe could also create a directory in /tmp that jane couldn't remove. [/COLOR][/SIZE][/FONT]


Hope that helps,

Phill.

---

### Post by alphaniner on 2009-10-26
I think the sticky bit only works with directories.

Edit: From **man chmod**

> RESTRICTED DELETION FLAG OR STICKY BIT
       The  restricted  deletion  flag  or  sticky  bit is a single bit, whose
       interpretation depends on the file type.  **For directories**, it  prevents
       unprivileged  users  from  removing or renaming a file in the directory
       unless they  own  the  file  or  the  directory;  this  is  called  the
       restricted  deletion  flag  for the directory, and is commonly found on
       world-writable directories like /tmp.  [B]For regular files on some  older
       systems,[/B]  the  bit saves the program&#8217;s text image on the swap device so
       it will load more quickly when run; this is called the sticky bit.

---

### Post by sahabcse on 2009-10-27
Finally I have assign sticky bit permission for one directory and the details are 

===========================================
ubuntu@sahab-desktop:~$ mkdir files
ubuntu@sahab-desktop:~$ chmod 1775 files/
ubuntu@sahab-desktop:~$ ls -al
total 28
drwxr-xr-x 3 ubuntu ubuntu  264 2009-10-27 10:34 .
drwxr-xr-x 5 root   root    120 2009-10-26 15:28 ..
-rw------- 1 ubuntu ubuntu  284 2009-10-27 09:59 .bash_history
-rw-r--r-- 1 ubuntu ubuntu  220 2009-10-26 15:28 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3115 2009-10-26 15:28 .bashrc
-rw-r--r-- 1 ubuntu ubuntu  357 2009-10-26 15:28 examples.desktop
drwxrwxr-t 2 ubuntu   1001   48 2009-10-27 10:34 files
-rw-r--r-- 1 ubuntu ubuntu  675 2009-10-26 15:28 .profile
-rwxrwxr-t 1 ubuntu ubuntu   10 2009-10-26 15:28 test
-rw------- 1 ubuntu ubuntu  584 2009-10-26 15:28 .viminfo
ubuntu@sahab-desktop:~$ cd files/
ubuntu@sahab-desktop:~/files$ touch ubuntu
============================================================

Then I have login to the user sahab create one file under stick bit folder and try to remove the file ubuntu (it was created by ubuntu user) its not allowed delete

sahab@sahab-desktop:~$ cd /home/ubuntu/files/
sahab@sahab-desktop:/home/ubuntu/files$ touch sahab
sahab@sahab-desktop:/home/ubuntu/files$ rm -rf ubuntu 
rm: cannot remove `ubuntu': Operation not permitted

After that I try to remove the file sahab (it was created by the user sahab) in the user ubuntu, that time its not showing error message, the file also deleted, My doubt is that owner of the sticky bit can delete all the other user created files?

ubuntu@sahab-desktop:~/files$ ls
sahab  ubuntu
ubuntu@sahab-desktop:~/files$ rm -rf sahab 
ubuntu@sahab-desktop:~/files$ ls
ubuntu
ubuntu@sahab-desktop:~/files$

---

