---
title: "Ubuntu Default Home Folder Location ?"
date: 2010-07-11
forum: General Help
---

### Post by jman6495 on 2010-07-11
Hi
I was just wondering , when you create a new user , where are the files that make it ? , like the "default" home folder?
i was just curious , any help would be much appriciated

       -jman6495

---

### Post by texaswriter on 2010-07-11
I would have to imagine a script creates a series of files and folders. Considering most directories start with blank directories and / or blank files, this seems plausible. Though, because it is a wide array of programs with directories, the real way could be a combination of cached files/folders and scripted mkdir... etc 

For example, if you delete certain files / folders in your  .gnome and other gnome/gtk folders that are in you /home/$user folder you will find your settings get set to the default [original configuration]. This is one notable way to reset your menu bars. 

Hopefully a developer who knows first-hand can shed some more light on this.

---

### Post by QLee on 2010-07-11
> **jman6495 said:**
> Hi
I was just wondering , when you create a new user , where are the files that make it ? , like the "default" home folder?
i was just curious , any help would be much appriciated

According to the Linux file system hierarchy, they (home folder you asked about)  should be in,
 /etc/skel/.

---

### Post by jman6495 on 2010-07-12
unfortionatly not , well , the files must be created elsewhere because there is only the "examples" folder

---

### Post by maple on 2010-07-17
they are in the /etc/skel directory

google questions that are this simple.

---

### Post by bodhi.zazen on 2010-07-17
> **jman6495 said:**
> unfortionatly not , well , the files must be created elsewhere because there is only the "examples" folder

If you create a new user and then list the new users directory, without first logging in, all that will be in the new home are the files from /etc/skel

```
root@ufbt:~#[COLOR=navy]adduser test[/COLOR]
Adding user `test' ...
Adding new group `test' (1001) ...
Adding new user `test' (1001) with group `test' ...
Creating home directory `/home/test' ...
**[COLOR=darkred]Copying files from `/etc/skel' ...[/COLOR]**
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] y

[COLOR=green]root@ufbt:~#ls **/home/test** -la
total 24
drwxr-xr-x 2 test test 4096 2010-07-16 22:36 .
drwxr-xr-x 5 root root 4096 2010-07-16 22:36 ..
-rw-r--r-- 1 test test  220 2010-07-16 22:36 .bash_logout
-rw-r--r-- 1 test test 3103 2010-07-16 22:36 .bashrc
-rw-r--r-- 1 test test  179 2010-07-16 22:36 examples.desktop
-rw-r--r-- 1 test test  675 2010-07-16 22:36 .profile[/COLOR]

[COLOR=blue]root@ufbt:~#ls **/etc/skel** -la
total 32
drwxr-xr-x   2 root root  4096 2010-06-06 00:38 .
drwxr-xr-x 128 root root 12288 2010-07-16 22:36 ..
-rw-r--r--   1 root root   220 2010-06-06 00:37 .bash_logout
-rw-r--r--   1 root root  3103 2010-06-06 00:37 .bashrc
-rw-r--r--   1 root root   179 2010-06-06 00:37 examples.desktop
-rw-r--r--   1 root root   675 2010-06-06 00:37 .profile[/COLOR]
```The other config files are set by various applications and most are in /usr/share , often by application name.

---

### Post by jman6495 on 2010-07-17
> **bodhi.zazen said:**
> If you create a new user and then list the new users directory, without first logging in, all that will be in the new home are the files from /etc/skel

```
root@ufbt:~#[COLOR=navy]adduser test[/COLOR]
Adding user `test' ...
Adding new group `test' (1001) ...
Adding new user `test' (1001) with group `test' ...
Creating home directory `/home/test' ...
**[COLOR=darkred]Copying files from `/etc/skel' ...[/COLOR]**
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] y

[COLOR=green]root@ufbt:~#ls **/home/test** -la
total 24
drwxr-xr-x 2 test test 4096 2010-07-16 22:36 .
drwxr-xr-x 5 root root 4096 2010-07-16 22:36 ..
-rw-r--r-- 1 test test  220 2010-07-16 22:36 .bash_logout
-rw-r--r-- 1 test test 3103 2010-07-16 22:36 .bashrc
-rw-r--r-- 1 test test  179 2010-07-16 22:36 examples.desktop
-rw-r--r-- 1 test test  675 2010-07-16 22:36 .profile[/COLOR]

[COLOR=blue]root@ufbt:~#ls **/etc/skel** -la
total 32
drwxr-xr-x   2 root root  4096 2010-06-06 00:38 .
drwxr-xr-x 128 root root 12288 2010-07-16 22:36 ..
-rw-r--r--   1 root root   220 2010-06-06 00:37 .bash_logout
-rw-r--r--   1 root root  3103 2010-06-06 00:37 .bashrc
-rw-r--r--   1 root root   179 2010-06-06 00:37 examples.desktop
-rw-r--r--   1 root root   675 2010-06-06 00:37 .profile[/COLOR]
```The other config files are set by various applications and most are in /usr/share , often by application name.

thanks , it worked ! this community is amazing

---

### Post by bodhi.zazen on 2010-07-17
> **jman6495 said:**
> thanks , it worked ! this community is amazing

If you wish, you can add files to /etc/skel and any additional files will also be copied when you create a new user.

---

