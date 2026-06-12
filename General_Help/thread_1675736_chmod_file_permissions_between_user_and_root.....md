---
title: "chmod file permissions between user and root...."
date: 2011-01-26
forum: General Help
---

### Post by abhilashm86 on 2011-01-26
I want to have two kind of users in a work machine having ubuntu 10.04, 

1) He is the admin, have sudo privilages and install, do all types of work, his username is abhilash 

2) A user who is normally a IT administrator, who can just install or remove softwares, but cannot access files of abhilash. 
I'm trying to do this and my head is going blank, so please help!! The problem where i'm stuck is, if IT admin can install softwares, then he can become sudo as sudo su, then he can view my files :(

So here is a small test i did, first with abhilash. 
```
abhilash@abhilash-G62:/home/abhilash/Documents$ ls -l
total 4
-rw------- 1 abhilash abhilash 27 2010-11-19 07:22 softwares_info

```

Now others and group don't have any permissions!! But when IT Administrator becomes root, he can see this file:( 

```
test@abhilash-G62:/home/abhilash/Documents$ sudo su
root@abhilash-G62:/home/abhilash/Documents# cat softwares_info 
<
loads of file info
>
root@abhilash-G62:/home/abhilash/Documents# exit
test@abhilash-G62:/home/abhilash/Documents$ cat softwares_info 
cat: softwares_info: Permission denied
test@abhilash-G62:/home/abhilash/Documents$ 

```

Please help with this, since I tried searching and atlast got frustrated!!

---

### Post by djeikyb on 2011-01-26
(1) Giving sudo access to a user you wanted restricted is wrong.

(2) Create a new group that has only install privileges.

I don't know how to do 2 yet, but I think that answer is right.

---

### Post by abhilashm86 on 2011-01-26
> **djeikyb said:**
> (1) Giving sudo access to a user you wanted restricted is wrong.

(2) Create a new group that has only install privileges.

I don't know how to do 2 yet, but I think that answer is right.

I'm the admin of system, so that feature is for me. 

How exactly can i create a group that has right only to install softwares?? To install something, he should have sudo privilages.........

---

### Post by djeikyb on 2011-01-26
Like I said, I don't know.

But that is beside the point, because I found a spare five minutes to google your problem, and found that my assertion in 1 is wrong. Sudo is precisely the tool you want, because you can limit what programs each sudo-ified user can use. Pretty sweet actually. I haven't played much with configuring sudo, but now I'm impressed.

These links explain things way better than I could:

[http://linsec.ca/Using_Sudo_to_Limit_Access](http://linsec.ca/Using_Sudo_to_Limit_Access)
[http://serverfault.com/questions/36759/editing-sudoers-file-to-restrict-a-users-commands](http://serverfault.com/questions/36759/editing-sudoers-file-to-restrict-a-users-commands)
[http://www.google.com/search?q=sudo+limit+access+to+commands](http://www.google.com/search?q=sudo+limit+access+to+commands)

---

### Post by abhilashm86 on 2011-01-26
> **djeikyb said:**
> Like I said, I don't know.

But that is beside the point, because I found a spare five minutes to google your problem, and found that my assertion in 1 is wrong. Sudo is precisely the tool you want, because you can limit what programs each sudo-ified user can use. Pretty sweet actually. I haven't played much with configuring sudo, but now I'm impressed.

These links explain things way better than I could:

[http://linsec.ca/Using_Sudo_to_Limit_Access](http://linsec.ca/Using_Sudo_to_Limit_Access)
[http://serverfault.com/questions/36759/editing-sudoers-file-to-restrict-a-users-commands](http://serverfault.com/questions/36759/editing-sudoers-file-to-restrict-a-users-commands)
[http://www.google.com/search?q=sudo+limit+access+to+commands](http://www.google.com/search?q=sudo+limit+access+to+commands)

Hey glad you understood my problem, this is most brain tweaking thing i did on ubuntu, yep still trying around!! Yes i'll look at the resources you've mentioned. 

And i saw we can restrict what commands one may run with sudo, by editing /etc/sudoers. So i'll be back if i find a solution!!

---

### Post by abhilashm86 on 2011-01-26
Finally solved the problem, thanks for everyone helping!! 
I'll post contents of my /etc/sudoers file, just to show small tweaks i did, 
To open /etc/sudoers file, 
sudo su
then, 
root@abhilash-G62:/home/abhilash# export EDITOR=gedit; visudo

```

Defaults	env_reset

# Host alias specification

# User alias specification
User_Alias        BINADMIN = test




# Cmnd alias specification
Cmnd_Alias         SU = /bin/hostname, /etc/apache2, /usr/bin/apt-get


# User privilege specification
root	ALL=(ALL) ALL
BINADMIN	ALL = SU

```

Then i did a check with my other user called test........
```
abhilash@abhilash-G62:~$ su test
Password: 
test@abhilash-G62:/home/abhilash$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vim-runtime
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim vim-runtime
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 6,563kB of archives.
After this operation, 27.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 

``` 

But see the following commands, 
```
test@abhilash-G62:/home/abhilash/Documents$ ls -l
total 4
-rw------- 1 abhilash abhilash 27 2010-11-19 07:22 softwares_info
test@abhilash-G62:/home/abhilash/Documents$ cat softwares_info 
cat: softwares_info: Permission denied
test@abhilash-G62:/home/abhilash/Documents$ sudo cat softwares_info 
Sorry, user test is not allowed to execute '/bin/cat softwares_info' as root on abhilash-G62.
test@abhilash-G62:/home/abhilash/Documents$ 

```

Ubuntu is so flexible when it comes to a work machine!! ubuntu rocks:guitar::lolflag:

---

