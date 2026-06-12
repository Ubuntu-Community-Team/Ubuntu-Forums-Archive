---
title: "ubuntu minimal install ate 21GB"
date: 2011-12-16
forum: General Help
---

### Post by elliotn on 2011-12-16
here is my df -h 
```
elliotn@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              49G   21G   26G  46% /
udev                  993M  4.0K  993M   1% /dev
tmpfs                 401M  752K  401M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1003M  892K 1002M   1% /run/shm
elliotn@ubuntu:~$ 

```

I only installed the basics, like ubuntu desktop, lxde,ff, rythmbox, audacious, ccsm, bleachbit, remastersys(yet to use it) software center, synaptic, gstreamer codes,vlc, conky. 

I have no personal file in my home, it is only the system files only, no games etc 

why 21GB

---

### Post by SlugSlug on 2011-12-16
> **elliotn said:**
> here is my df -h 
```
elliotn@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              49G   21G   26G  46% /
udev                  993M  4.0K  993M   1% /dev
tmpfs                 401M  752K  401M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1003M  892K 1002M   1% /run/shm
elliotn@ubuntu:~$ 

```I only installed the basics, like ubuntu desktop, lxde,ff, rythmbox, audacious, ccsm, bleachbit, remastersys(yet to use it) software center, synaptic, gstreamer codes,vlc, conky. 

I have no personal file in my home, it is only the system files only, no games etc 

why 21GB


Could you post output of 
```
sudo du / -sch 
```

---

### Post by elliotn on 2011-12-16
> **SlugSlug said:**
> Could you post output of 
```
sudo du / -sch 
```

elliotn@ubuntu:~$ sudo du / -sch
[sudo] password for elliotn: 
du: cannot access `/home/elliotn/.gvfs': Permission denied
du: cannot access `/proc/2533/task/2533/fd/3': No such file or directory
du: cannot access `/proc/2533/task/2533/fdinfo/3': No such file or directory
du: cannot access `/proc/2533/fd/3': No such file or directory
du: cannot access `/proc/2533/fdinfo/3': No such file or directory
29G	/
29G	total
elliotn@ubuntu:~$

---

### Post by SlugSlug on 2011-12-16
hum,

```

cd /
 sudo du * -sch
```

---

### Post by elliotn on 2011-12-16
> **SlugSlug said:**
> Could you post output of 
```
sudo du / -sch 
```

```
elliotn@ubuntu:~$ sudo du / -sch
[sudo] password for elliotn: 
du: cannot access `/home/elliotn/.gvfs': Permission denied
du: cannot access `/proc/2533/task/2533/fd/3': No such file or directory
du: cannot access `/proc/2533/task/2533/fdinfo/3': No such file or directory
du: cannot access `/proc/2533/fd/3': No such file or directory
du: cannot access `/proc/2533/fdinfo/3': No such file or directory
29G	/
29G	total
elliotn@ubuntu:~$ 



```

---

### Post by SlugSlug on 2011-12-16
> **elliotn said:**
> ```
elliotn@ubuntu:~$ sudo du / -sch
[sudo] password for elliotn: 
du: cannot access `/home/elliotn/.gvfs': Permission denied
du: cannot access `/proc/2533/task/2533/fd/3': No such file or directory
du: cannot access `/proc/2533/task/2533/fdinfo/3': No such file or directory
du: cannot access `/proc/2533/fd/3': No such file or directory
du: cannot access `/proc/2533/fdinfo/3': No such file or directory
29G    /
29G    total
elliotn@ubuntu:~$ 



```


no my second post was 

```
cd /
```then
```
sudo du * -sch
```

should  display a list of folders and the sizes

---

### Post by elliotn on 2011-12-16
> **SlugSlug said:**
> hum,

```

cd /
 sudo du * -sch
```

```
elliotn@ubuntu:~$ cd /
elliotn@ubuntu:/$ sudo du * -sch
[sudo] password for elliotn: 
8.4M	bin
29M	boot
4.0K	dev
15M	etc
du: cannot access `home/elliotn/.gvfs': Permission denied
137M	home
0	initrd.img
167M	lib
16K	lost+found
7.7G	media
4.0K	mnt
4.0K	opt
du: cannot access `proc/6620/task/6620/fd/3': No such file or directory
du: cannot access `proc/6620/task/6620/fdinfo/3': No such file or directory
du: cannot access `proc/6620/fd/3': No such file or directory
du: cannot access `proc/6620/fdinfo/3': No such file or directory
0	proc
19G	root
856K	run
11M	sbin
4.0K	selinux
4.0K	srv
0	sys
52K	tmp
1.3G	usr
370M	var
0	vmlinuz
29G	total
elliotn@ubuntu:/$ 

```

---

### Post by 3rdalbum on 2011-12-16
EDIT: Whatever you have mounted currently, unmount it (/media is showing as 7 gigs used). Does the df -h output change?

If so, then the 7 gigs used in /media isn't actually used on / - so it's not your Linux disk space, it's just that your external drives are being counted as part of the total.

---

### Post by SlugSlug on 2011-12-16
```
sudo -i 
```


```
ls -lah /root/
```

---

### Post by snowpine on 2011-12-16
You have 19gb in /root which is very strange. Maybe there is junk in the root trash can? If so just do a forum Search on "empty root trash"; it is a frequently-asked question.

---

### Post by elliotn on 2011-12-16
> **SlugSlug said:**
> ```
sudo -i 
```


```
ls -lah /root/
```

```


elliotn@ubuntu:~$ sudo -i
root@ubuntu:~# ls -lah /root /
/:
total 92K
drwxr-xr-x  22 root root 4.0K 2011-12-08 09:27 .
drwxr-xr-x  22 root root 4.0K 2011-12-08 09:27 ..
drwxr-xr-x   2 root root 4.0K 2011-12-05 15:29 bin
drwxr-xr-x   3 root root 4.0K 2011-12-04 19:17 boot
drwxr-xr-x  15 root root 4.3K 2011-12-16 17:59 dev
drwxr-xr-x 130 root root  12K 2011-12-16 17:59 etc
drwxr-xr-x   4 root root 4.0K 2011-12-02 17:01 home
lrwxrwxrwx   1 root root   33 2011-12-01 14:07 initrd.img -> /boot/initrd.img-3.0.0-13-generic
drwxr-xr-x  22 root root 4.0K 2011-12-02 16:09 lib
drwx------   2 root root  16K 2011-12-01 13:48 lost+found
drwxr-xr-x   5 root root 4.0K 2011-12-16 17:59 media
drwxr-xr-x   2 root root 4.0K 2011-10-09 09:29 mnt
drwxr-xr-x   2 root root 4.0K 2011-12-01 13:54 opt
dr-xr-xr-x 141 root root    0 2011-12-16 19:44 proc
drwx------  17 root root 4.0K 2011-12-08 10:49 root
drwxr-xr-x  17 root root  620 2011-12-16 17:47 run
drwxr-xr-x   2 root root 4.0K 2011-12-02 16:09 sbin
drwxr-xr-x   2 root root 4.0K 2011-06-21 20:43 selinux
drwxr-xr-x   2 root root 4.0K 2011-12-01 13:54 srv
drwxr-xr-x  12 root root    0 2011-12-16 19:44 sys
drwxrwxrwt  12 root root 4.0K 2011-12-16 18:10 tmp
drwxr-xr-x  10 root root 4.0K 2011-12-01 13:54 usr
drwxr-xr-x  12 root root 4.0K 2011-12-15 13:28 var
lrwxrwxrwx   1 root root   29 2011-12-01 14:07 vmlinuz -> boot/vmlinuz-3.0.0-13-generic

/root:
total 88K
drwx------ 17 root root 4.0K 2011-12-08 10:49 .
drwxr-xr-x 22 root root 4.0K 2011-12-08 09:27 ..
-rw-------  1 root root  314 2011-12-16 17:51 .bash_history
-rw-r--r--  1 root root 3.1K 2011-07-08 19:13 .bashrc
drwx------  5 root root 4.0K 2011-12-08 15:41 .cache
drwx------ 12 root root 4.0K 2011-12-08 15:41 .config
drwx------  3 root root 4.0K 2011-12-02 06:09 .dbus
drwxr-xr-x  3 root root 4.0K 2011-12-08 15:43 Desktop
drwx------  2 root root 4.0K 2011-12-05 12:35 .gconf
drwxr-xr-x  4 root root 4.0K 2011-12-02 11:27 .gnome2
drwx------  2 root root 4.0K 2011-12-02 11:27 .gnome2_private
drwxr-xr-x  2 root root 4.0K 2011-12-08 10:49 .gstreamer-0.10
drwx------  2 root root 4.0K 2011-12-08 10:49 .gvfs
drwx------  3 root root 4.0K 2011-12-02 06:13 .local
drwx------  4 root root 4.0K 2011-12-02 11:27 .mozilla
-rw-r--r--  1 root root 2.1K 2011-12-02 06:44 .photorec.cfg
drwxr-xr-x  3 root root 4.0K 2011-12-02 11:29 Pictures
-rw-r--r--  1 root root  140 2011-07-08 19:13 .profile
drwx------  2 root root 4.0K 2011-12-16 17:45 .pulse
-rw-------  1 root root  256 2011-12-02 13:46 .pulse-cookie
drwx------  3 root root 4.0K 2011-12-05 15:29 .synaptic
drwx------  4 root root 4.0K 2011-12-08 10:56 .thumbnails
root@ubuntu:~# 


```

---

### Post by SlugSlug on 2011-12-16
> **elliotn said:**
> ```




/root:
total 88K
drwx------ 17 root root 4.0K 2011-12-08 10:49 .
drwxr-xr-x 22 root root 4.0K 2011-12-08 09:27 ..
-rw-------  1 root root  314 2011-12-16 17:51 .bash_history
-rw-r--r--  1 root root 3.1K 2011-07-08 19:13 .bashrc
drwx------  5 root root 4.0K 2011-12-08 15:41 .cache
drwx------ 12 root root 4.0K 2011-12-08 15:41 .config
drwx------  3 root root 4.0K 2011-12-02 06:09 .dbus
drwxr-xr-x  3 root root 4.0K 2011-12-08 15:43 Desktop
drwx------  2 root root 4.0K 2011-12-05 12:35 .gconf
drwxr-xr-x  4 root root 4.0K 2011-12-02 11:27 .gnome2
drwx------  2 root root 4.0K 2011-12-02 11:27 .gnome2_private
drwxr-xr-x  2 root root 4.0K 2011-12-08 10:49 .gstreamer-0.10
drwx------  2 root root 4.0K 2011-12-08 10:49 .gvfs
drwx------  3 root root 4.0K 2011-12-02 06:13 .local
drwx------  4 root root 4.0K 2011-12-02 11:27 .mozilla
-rw-r--r--  1 root root 2.1K 2011-12-02 06:44 .photorec.cfg
drwxr-xr-x  3 root root 4.0K 2011-12-02 11:29 Pictures
-rw-r--r--  1 root root  140 2011-07-08 19:13 .profile
drwx------  2 root root 4.0K 2011-12-16 17:45 .pulse
-rw-------  1 root root  256 2011-12-02 13:46 .pulse-cookie
drwx------  3 root root 4.0K 2011-12-05 15:29 .synaptic
drwx------  4 root root 4.0K 2011-12-08 10:56 .thumbnails
root@ubuntu:~# 


```


right ok 

sudo -i  if u exited that terminal

```
cd /root
``````
du * -sch 
```looks like u have logged in as root

---

### Post by elliotn on 2011-12-16
> **snowpine said:**
> You have 19gb in /root which is very strange. Maybe there is junk in the root trash can? If so just do a forum Search on "empty root trash"; it is a frequently-asked question.

I have emptied root trash

---

### Post by SlugSlug on 2011-12-16
> **elliotn said:**
> I have emptied root trash


so is this solved?

---

### Post by snowpine on 2011-12-16
Problem solved? :)

---

### Post by elliotn on 2011-12-16
> **snowpine said:**
> Problem solved? :)

no it ain't solved yet I still have 21GB used by file system

---

### Post by SlugSlug on 2011-12-16
right ok 

sudo -i  if u exited that terminal

     cd /root 
 
     du * -sch

---

### Post by elliotn on 2011-12-16
> **SlugSlug said:**
> right ok 

sudo -i  if u exited that terminal

     cd /root 
 
     du * -sch

```
root@ubuntu:~# sudo -i
root@ubuntu:~# cd/root
-bash: cd/root: No such file or directory
root@ubuntu:~# cd /root
root@ubuntu:~# du* -sch
No command 'du*' found, did you mean:
 Command 'du' from package 'coreutils' (main)
du*: command not found
root@ubuntu:~# du*-sch
du*-sch: command not found
root@ubuntu:~# du *-sch
du: cannot access `*-sch': No such file or directory
root@ubuntu:~# 

```

---

### Post by SlugSlug on 2011-12-16
> **elliotn said:**
> ```
root@ubuntu:~# sudo -i
root@ubuntu:~# cd/root
-bash: cd/root: No such file or directory
root@ubuntu:~# cd /root
root@ubuntu:~# du* -sch
No command 'du*' found, did you mean:
 Command 'du' from package 'coreutils' (main)
du*: command not found
root@ubuntu:~# du*-sch
du*-sch: command not found
root@ubuntu:~# du *-sch
du: cannot access `*-sch': No such file or directory
root@ubuntu:~# 

```


its 

```
du * -sch 
```


use copy and paste ;)

---

### Post by elliotn on 2011-12-16
> **SlugSlug said:**
> its 

```
du * -sch 
```


use copy and paste ;)

```
elliotn@ubuntu:~$ sudo -i
[sudo] password for elliotn: 
root@ubuntu:~# du * -sch
17G	Desktop
8.0K	Pictures
17G	total
root@ubuntu:~# 


```

and my desktop is empty. no hidden files

---

### Post by jerome1232 on 2011-12-16
rinse and repeat, your desktop might be empty, but apparently roots isn't.
```

sudo du /root/Desktop -h --max-depth=1

```

It's probably safe to just delete what is in /root/Desktop, but I just want to make sure it's not your pictures or music or something you might want to keep first.

---

### Post by snowpine on 2011-12-16
Something is very wrong if you are storing personal documents/files in your /root folder. Please read the Ubuntu recommendations regarding root account: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jerome1232 on 2011-12-16
> **snowpine said:**
> Something is very wrong if you are storing personal documents/files in your /root folder. Please read the Ubuntu recommendations regarding root account: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If these forums still had a thanks feature, I'd be clicking it on your post, heck, I'm virtually clicking the imaginary thanks button.

---

### Post by snowpine on 2011-12-16
> **jerome1232 said:**
> If these forums still had a thanks feature, I'd be clicking it on your post, heck, I'm virtually clicking the imaginary thanks button.

Stop it, that tickles! :D

---

### Post by SlugSlug on 2011-12-16
> **elliotn said:**
> ```
elliotn@ubuntu:~$ sudo -i
[sudo] password for elliotn: 
root@ubuntu:~# du * -sch
17G    Desktop
8.0K    Pictures
17G    total
root@ubuntu:~# 


```and my desktop is empty. no hidden files

sudo -i 

ls -lah /root/Desktop/

---

### Post by elliotn on 2011-12-16
> **jerome1232 said:**
> rinse and repeat, your desktop might be empty, but apparently roots isn't.
```

sudo du /root/Desktop -h --max-depth=1

```

It's probably safe to just delete what is in /root/Desktop, but I just want to make sure it's not your pictures or music or something you might want to keep first.

thanks a lot all of u. I had 19Gb folder in my root desktop, it was a Windows backup I have made.... were is the thanks button when u need it. solved

---

