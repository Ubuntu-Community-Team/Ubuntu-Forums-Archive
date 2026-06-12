---
title: "External hard disk read-only problem"
date: 2011-11-24
forum: General Help
---

### Post by hrok on 2011-11-24
I have an external hard drive that was named "My Passport" with a whitespace and i wanted to get rid of that whitespace because it was causing trouble. So i renamed it to "repository" on a windows machine because at that time it seemed the easiest way to do that. Than i started to get errors on my linux machine that the disk is read-only file system. The ls -l gives me

rok@stroj:~$ ls -l /media/
total 8
drwxr-xr-x 2 root root 4096 2011-10-17 19:16 isoImage
dr-x------ 1 rok  rok  4096 2011-11-20 12:23 repository

and if i try to change the permissions as root i get

root@stroj:~# chmod +w /media/repository/
chmod: changing permissions of `/media/repository/': Read-only file system

So now i can't really use the disk on my linux machine that i primarily use. How can i solve this?

---

### Post by BC59 on 2011-11-24
Why you don't get the HDD to a Windows machine, to format it in NTFS, to be sure it's going to be readable by both Win and Linux?

---

### Post by hrok on 2011-11-24
It is readable on both systems but since i renamed it i somehow lost the writing permission on linux. I am asking how to change the selfproclaimed read-only status. And formatting the disk is kind of a last resort because the disk contains quite a lot of data and i don't really have any empty disks lying around.

---

### Post by BC59 on 2011-11-24
You can only change permissions through windows.

---

### Post by hrok on 2011-11-25
Yes but windows doesn't allow me to do that either for some reason. It says that it changed permissions but in reality it just stays as it was and it has some problems with names of directories having some for windows illegal characters. Is there really no way to cancel the read-only status of the disk in linux?

---

### Post by BC59 on 2011-11-25
I'm not sure if you can but look here:

[http://ubuntuforums.org/showthread.php?t=1446788](http://ubuntuforums.org/showthread.php?t=1446788)

---

### Post by hrok on 2011-11-25
Thank you, that link answered my questions.

---

