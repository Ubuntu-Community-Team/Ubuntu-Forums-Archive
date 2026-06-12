---
title: "file / folder permissions tweek - help"
date: 2009-12-19
forum: General Help
---

### Post by ian2112 on 2009-12-19
Hello,

I am seeking a method of having all files in a directory (and its subdirectories) inherit the file permissions of that directory any time they are moved or copied into that directory.

Background: I have two users (Jack 'n Jill) and I've set up a /media/shared directory.  This directory belongs to the group "Users" and Jack 'n Jill both belong to this group.  I want to configure my system such that anytime Jack or Jill copy a file into /media/shared (or its subdirectories) that file will now belong to the group "Users".

The challenge is that (by default?) whenever Jack or Jill are logged in, any file one creates is set with the group (and user) "Jack" or "Jill" as the case may be.

In short, I'd like to have a directory where both users can share files have full permissions.

Is this possible to achieve without a script?

Any help would be appreciated.  Thanks in advance.

Ian.

---

### Post by joes7 on 2009-12-19
Right Click. Properties. Go to the "Permissions" tab. Applyc your changes.

---

### Post by Lukas666 on 2009-12-19
> **ian2112 said:**
> Hello,

I am seeking a method of having all files in a directory (and its subdirectories) inherit the file permissions of that directory any time they are moved or copied into that directory.

Background: I have two users (Jack 'n Jill) and I've set up a /media/shared directory.  This directory belongs to the group "Users" and Jack 'n Jill both belong to this group.  I want to configure my system such that anytime Jack or Jill copy a file into /media/shared (or its subdirectories) that file will now belong to the group "Users".

The challenge is that (by default?) whenever Jack or Jill are logged in, any file one creates is set with the group (and user) "Jack" or "Jill" as the case may be.

In short, I'd like to have a directory where both users can share files have full permissions.

Is this possible to achieve without a script?

Any help would be appreciated.  Thanks in advance.

Ian.

Here is your friend: umask

---

### Post by sisco311 on 2009-12-19
You have to enable ACL support for the partition.

[list=i]

[*] Install ACL

open a terminal and run:
```
sudo apt-get install acl
```

[*] Edit the fstab file:
```
gksu gedit /etc/fstab
```
and add the acl flag to the partition's mount options:

```
UUID=<...>    /media/shared    ext3    relatime,**acl**    0    2
```    

[*] Remount the partition to activate ACL support:
```
sudo mount -o remount /media/shared
``` 

[*] Set the permissions:
```
sudo setfacl -Rdm g:**users**:rwx /media/shared
sudo setfacl -Rm g:**users**:rwx /media/shared
```

[*] done :)

[/list]


[https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport]("https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport")

---

### Post by malbertocuao on 2009-12-19
Hi .

You must try share the directory with samba and use it as if you were on the network.

The settings in samba would looks like:

[shared]
comment = Data
path = /media/shared
force user = Jack
force group = users
read only = No
guest ok = Yes
inherit permissions = Yes

---

### Post by joes7 on 2009-12-19
Log in as your root user.

---

### Post by ian2112 on 2009-12-19
Thanks for the help everyone.  A few things here to try.

One thing I should clarify is that my /media/shared is not a separate partition.

Perhaps it should be; is there much risk to creating a new partition?  

More later...

---

### Post by sisco311 on 2009-12-19
> **ian2112 said:**
> Thanks for the help everyone.  A few things here to try.

One thing I should clarify is that my /media/shared is not a separate partition.

Perhaps it should be; is there much risk to creating a new partition?  

More later...

Then activate the ACL support on the partition on which the directory is stored.

---

### Post by ian2112 on 2009-12-19
So far no luck using ACL.  I believe I've correctly installed it and set the defaults for the directory, but if I move a file from "Jack's" desktop to the /media/shared directory, it remains belonging to the group "Jack".  Until I change the file to belong to the group "users", then user "Jill" will only have the permissions associated with Other...

Perhaps I need to create a script... 

Thoughts?

---

### Post by sisco311 on 2009-12-20
> **ian2112 said:**
> So far no luck using ACL.  I believe I've correctly installed it and set the defaults for the directory, but if I move a file from "Jack's" desktop to the /media/shared directory, it remains belonging to the group "Jack".  Until I change the file to belong to the group "users", then user "Jill" will only have the permissions associated with Other...

Perhaps I need to create a script... 

Thoughts?

what's the output of:
```
getfacl /media/shared
```

---

### Post by ian2112 on 2009-12-21
Here's the output - than-you for reviewing my configuration - much appreciated!

ian@ian-desktop:~$ sudo getfacl /media
getfacl: Removing leading '/' from absolute path names
# file: media
# owner: root
# group: root
user::rwx
group::r-x
group:users:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::r-x
default:group:users:rwx
default:mask::rwx
default:other::r-x

---

### Post by sisco311 on 2009-12-21
> **ian2112 said:**
> Here's the output - than-you for reviewing my configuration - much appreciated!

ian@ian-desktop:~$ sudo getfacl /media
getfacl: Removing leading '/' from absolute path names
# file: media
# owner: root
# group: root
user::rwx
group::r-x
**group:users:rwx**
mask::rwx
other::r-x
default:user::rwx
default:group::r-x
**default:group:users:rwx**
default:mask::rwx
default:other::r-x

It looks okay, but you only have to set the permissions on the /media/shared directory. You can remove the extended acl entries from the /media directory:
```
sudo setfacl -Rkb /media
```

Then (re)set the permissions on /media/shared.

Did you try to create new files as Jack and/or Jill?

```
sudo -u Jack touch /media/shared/newfile1
sudo -u Jill touch /media/shared/newfile2
```


[HOWTO: Access Control Lists (ACLs) in Linux]("http://www.youtube.com/watch?v=6piQXXHTmqk")

---

### Post by QLee on 2009-12-21
> **ian2112 said:**
> Hello,

I am seeking a method of having all files in a directory (and its subdirectories) inherit the file permissions of that directory any time they are moved or copied into that directory.

Background: I have two users (Jack 'n Jill) and I've set up a /media/shared directory.  This directory belongs to the group "Users" and Jack 'n Jill both belong to this group.  I want to configure my system such that anytime Jack or Jill copy a file into /media/shared (or its subdirectories) that file will now belong to the group "Users".

The challenge is that (by default?) whenever Jack or Jill are logged in, any file one creates is set with the group (and user) "Jack" or "Jill" as the case may be.

In short, I'd like to have a directory where both users can share files have full permissions.

Is this possible to achieve without a script?

Any help would be appreciated.  Thanks in advance.

Ian.

It looks like what you want to investigate is setgid for the folder.

---

### Post by sisco311 on 2009-12-21
> **QLee said:**
> It looks like what you want to investigate is setgid for the folder.

Setting the setgid permission on a directory causes new files and subdirectories created within it to inherit its gid, but the files don't inherit the group permissions.

---

### Post by ian2112 on 2009-12-21
Here's what I get when I try to create a file as each of the two users:

ian@ian-desktop:~$ sudo -u jodi touch /media/pictures/newfile1
[sudo] password for ian: 
ian@ian-desktop:~$ sudo -u ian touch /media/pictures/newfile2
ian@ian-desktop:~$ ls -l /media/pictures/
total 128
drwxrwx---+ 3 ian  users  4096 2009-11-22 20:49 HDR Photos
-rw-rwxr--+ 1 ian  ian   56167 2009-12-19 14:44 hogs_back_falls_5.jpg
-rw-rw----+ 1 jodi jodi      0 2009-12-21 17:21 newfile1
-rw-rw----+ 1 ian  ian       0 2009-12-21 17:21 newfile2
ian@ian-desktop:~$ 

What I'd like to have happen is that newfile1 and newfile2 iherit the group 'users'.  I think that would allow both users (Jack 'n Jill aka ian 'n jodi) to access and modify the files.

Just in case here's the getfacl on /media/pictures

ian@ian-desktop:~$ getfacl media/pictures/
getfacl: media/pictures/: No such file or directory
ian@ian-desktop:~$ getfacl /media/pictures/
getfacl: Removing leading '/' from absolute path names
# file: media/pictures/
# owner: root
# group: users
user::rwx
group::rwx
group:users:rwx
mask::rwx
other::---
default:user::rwx
default:group::rwx
default:group:users:rwx
default:mask::rwx
default:other::---

As before - the assistance is appreciated.

Ian

---

### Post by sisco311 on 2009-12-21
> **ian2112 said:**
> 

What I'd like to have happen is that newfile1 and newfile2 iherit the group 'users'.  I think that would allow both users (Jack 'n Jill aka ian 'n jodi) to access and modify the files.


As before - the assistance is appreciated.

Ian

The ls command displays the unix/linux file permissions.

ACLs extend the concept of unix/linux file permissions. 

newfile1 and newfile2 do inherit the group `users'. 

Just run:
```
getfacl /media/pictures/newfile1
```
it should return something like:
```
# file: media/pictures/newfile1
# owner: jodi
# group: jodi
user::rw-
group::r-x			#effective:r--
**group:users:rwx**		#effective:rw-
mask::rw-
other::r--

```

Oh, well, just try it out in the GUI. i.e. create a file as jodi and edit/remove it as ian.

EDIT: 

ACL = access control list, a list of users/groups with additional permissions.

---

### Post by ian2112 on 2009-12-22
Bingo!  As Jodi, I just opened and edited the Newfile2 that ian created.  It works.  Awesome.

Thank-you very much for all your help.

Ian.

---

