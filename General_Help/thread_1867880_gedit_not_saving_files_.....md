---
title: "gedit not saving files ...."
date: 2011-10-23
forum: General Help
---

### Post by raja.genupula on 2011-10-23
Hi I am using Xubuntu 11.10 ,Actually I am unable to save with and its giving as read-only file system. Look at that image , help me to close this problem .

Thanks in advance.

---

### Post by drs305 on 2011-10-23
It appears you do not have permission to write to that partition. You can probably select the 'Save As' option to save the file elsewhere (such as your HOME partition) or change how the partition is mounted so that you have read/write access to it.  

You also may be able to open gedit as root with "gksu gedit" but that would save any file with 'root' as the owner. I'm not sure it would work in this case regardless.

---

### Post by btindie on 2011-10-23
It's probably because the filesystem is mounted read-only or you do not have permission to write files there. What's the output of
```
mount | grep /media/alls
ls -ld /media/alls
```If it's an ext2/3/4 filesystem then it's probably owned by root for which your user account doesn't have permission to write to.

If you want everyone to be able to write to that partition then use
```
sudo chmod a=rwx /media/alls
```otherwise change the ownership to your user account
```
sudo chown raja:raja /media/alls
```Take a look at [this]("http://www.techrepublic.com/article/linux-file-and-directory-permissions/1047531") to learn more about file directory permissions.

---

### Post by raja.genupula on 2011-10-24
I don't know what happened because at the starting times it works fine , Because i am using Xubuntu from its Alpha release and moved to Beta and now final one .Up to now its good but from few days i getting this error , initially i thought that updates gonna help me to solve this issue but they haven't did that . 

Ok i will try the things in #3 and i will report you back what i have got after reaching to my room.

---

### Post by dcstar on 2011-10-24
> **raja.genupula said:**
> Hi I am using Xubuntu 11.10 ,Actually I am unable to save with and its giving as read-only file system. Look at that image , help me to close this problem .

Thanks in advance.

gedit only works correctly with Linux filesytems, Windows filesystems are **not** compatible with Linux apps like this.

---

### Post by raja.genupula on 2011-10-24
> **dcstar said:**
> gedit only works correctly with Linux filesytems, Windows filesystems are **not** compatible with Linux apps like this.

Hi man 
    But tell me up to now how i did all savings to that . No man this is not the reason and i think there is a problem with my filemanager.

---

### Post by raja.genupula on 2011-10-24
> **btindie said:**
> It's probably because the filesystem is mounted read-only or you do not have permission to write files there. What's the output of
```
mount | grep /media/alls
ls -ld /media/alls
```If it's an ext2/3/4 filesystem then it's probably owned by root for which your user account doesn't have permission to write to.

If you want everyone to be able to write to that partition then use
```
sudo chmod a=rwx /media/alls
```otherwise change the ownership to your user account
```
sudo chown raja:raja /media/alls
```Take a look at [this]("http://www.techrepublic.com/article/linux-file-and-directory-permissions/1047531") to learn more about file directory permissions.

hi man i have tried and got this

```
assassin@raju-xubuntu:~$ mount | grep /media/alls
/dev/sda4 on /media/alls type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
assassin@raju-xubuntu:~$ ls -ld /media/alls
dr-x------ 1 assassin assassin 12288 2011-10-15 20:28 /media/alls
assassin@raju-xubuntu:~$ sudo chmod a=rwx /media/alls
[sudo] password for assassin: 
chmod: changing permissions of `/media/alls': Read-only file system
assassin@raju-xubuntu:~$ sudo chown assassin:assassin /media/alls
chown: changing ownership of `/media/alls': Read-only file system

```

tried again and got the same problem.:(

---

### Post by Gatemaze on 2011-10-24
but from your ls output you don't have write permission....

do:
```

sudo chmod 744 /media/alls

```

and i hope this is not a usb pen with a "read-only" switch on it...

---

### Post by raja.genupula on 2011-10-24
> **Gatemaze said:**
> but from your ls output you don't have write permission....

do:
```

sudo chmod 744 /media/alls

```

and i hope this is not a usb pen with a "read-only" switch on it...

Hi man 
not done .....thinking to uninstalling file manager and re installing. ok i will get back to you with the result of it. . 
```
assassin@raju-xubuntu:~$ sudo chmod 744 /media/alls
chmod: changing permissions of `/media/alls': Read-only file system
```

---

### Post by raja.genupula on 2011-10-24
hmm this is really making me OFF .i have re-installed    fielmanager again but there is no result.

---

### Post by Gatemaze on 2011-10-24
What is the filesystem of the partition? To find out:
```

df -T

```

Also can you please do the following:
```

sudo touch /media/alls/foobar.txt

```
and see if you can create an empty file as root?

---

### Post by CatKiller on 2011-10-24
> **raja.genupula said:**
> hmm this is really making me OFF .i have re-installed    fielmanager again but there is no result.

Why would that help?

You've mounted your NTFS partition read-only. There are all sorts of guides for how to mount an NTFS partition read-write. Changing permissions won't help because NTFS can't handle permissions.

---

### Post by Gatemaze on 2011-10-24
also if it is ntfs as I've seen from your previous posts could you please check whether you have installed ntfs-3g and change your fstab entry to the following?
```

<your partition> /media/alls ntfs defaults,nls=utf8,umask=007,gid=1000 0 0

```

and then remount and tell me if it works. You might have mounted read-only (got to do with the mask and some flags if i recall well, but cant remember exactly what)....

---

### Post by raja.genupula on 2011-10-29
sometimes you know guys my Ubuntu works like crazy . this issue solved . I really dont know how but its gone . But one thing i can say that sometimes updates are the best solutions for the unknown issues.

---

