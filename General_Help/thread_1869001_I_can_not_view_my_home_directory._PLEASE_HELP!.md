---
title: "I can not view my home directory. PLEASE HELP!"
date: 2011-10-25
forum: General Help
---

### Post by Lisaac10 on 2011-10-25
I re-installed ubuntu 11.10 because Gnome 3 ruined my unity. I left everything how it was. I didn't delete my directories. But now I can't view it. How can I view my directory? I can't change the permissions and I have really important files in it :(

---

### Post by Erik1984 on 2011-10-25
How did you re-install everything? If your create a new user account during install it might not be the same as the owner of your old /home/user.

What does ```
ls -al /home 
``` say about the rights?

---

### Post by Erik1984 on 2011-10-25
btw you can always access your files through a Live-CD.

---

### Post by dino99 on 2011-10-25
as you said "home directory" i suppose you dont have formatted a /home partition, thats a bad idea as you have reinstalled the system and probably erased too your home "directory.

here is a standard installation:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ajgreeny on 2011-10-25
Did you have a separate /home partition?  If you did not, and home was just a folder in the root partition, I'm afraid it will now have been overwritten in the re-installation process.  You can try installing and running testdisk from a live CD, to try to recover the files etc etc, but you may find that at least some will now be gone for ever.

I hope you have a backup!

---

### Post by Lisaac10 on 2011-10-26
> **Euroman said:**
> How did you re-install everything? If your create a new user account during install it might not be the same as the owner of your old /home/user.

What does ```
ls -al /home 
``` say about the rights?

This is what I get:

stone@Rokuup:~$ ls -al /home
total 44
drwxr-xr-x  9 root  root   4096 2011-10-26 04:34 .
drwxr-xr-x 25 root  root   4096 2011-10-15 21:27 ..
lrwxrwxrwx  1 root  root     44 2011-10-26 04:34 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x  5 root  root   4096 2011-10-15 20:34 .ecryptfs
drwxrwxrwx 87  1001  1002  4096 2011-09-28 23:30 guest24
drwxr-xr-x  2 stone  1001  4096 2011-08-27 05:00 IGrullon
dr-x---rwx  2 stone  1002  4096 2011-08-01 01:54 ihelena
dr-x------  2  1003  1003  4096 2011-05-20 21:07 oshito
drwxr-x--- 90  1002  1002  4096 2011-10-15 20:09 oshitotakn
drwx------ 51 stone stone 12288 2011-10-26 04:48 stone

---

### Post by Vaphell on 2011-10-26
so which one is it?
does **gksu nautilus** let you enter it?

---

### Post by Lisaac10 on 2011-10-26
> **Vaphell said:**
> so which one is it?
does **gksu nautilus** let you enter it?

Stone is the one I'm currently using as my main user. I can't see Oshitotakn because it's from another group and it's only viewable by that group. But, I cat't find that group on user group settings. So I can't change the permissions. gksu nautilus doesn't let me see it :(

---

### Post by Vaphell on 2011-10-26
[http://linux.die.net/man/8/groupadd](http://linux.die.net/man/8/groupadd)
try
```
groupadd -g 1002 oshitotakn
```

another command worth looking is useradd, you can create a user and assign specific id
[http://linux.die.net/man/8/useradd](http://linux.die.net/man/8/useradd)

---

### Post by ajgreeny on 2011-10-26
This is all very odd!
Can you show the output of ```
who
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```one command at a time, just to check your system a bit more.

---

