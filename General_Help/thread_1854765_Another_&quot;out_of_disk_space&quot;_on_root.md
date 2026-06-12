---
title: "Another &quot;out of disk space&quot; on root"
date: 2011-10-05
forum: General Help
---

### Post by zielstep on 2011-10-05
All,

I can no longer run Update Manager because I'm getting the "Not enough free disk space" problem.

I'm learning on the fly, and while I have researched this issue for quite some time, I have absolutely no idea what to do.  It sounds like I need to delete some files somewhere, but I don't know what.

Can anyone please tell me what to type into terminal, and explain how I would know what to delete in the future?

Thank you for your help.

---

### Post by kuchera68 on 2011-10-05
To start out you can take a look at what directories are using the most space. You can issue the following command in a terminal (ctrl + alt + t)

```
> sudo du -h -c --max-depth=1 /
16K    /lost+found
26G    /media
170M    /lib
2.7G    /usr
....

```This will give you an idea where the most hard drive space is being used. In order to see the overall status of your partitions you can use df.

```
> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              69G   14G    53G  21% /
none                      2.0G  748K  2.0G   1% /dev
none                      2.0G  4.3M  2.0G   1% /dev/shm
none                      2.0G  156K  2.0G   1% /var/run
none                      2.0G     0     2.0G   0% /var/lock
/dev/sda5              96G   26G    71G  27% /media/VBox

```Post the results of these two commands and we'll see if there is a chance to reduce some of the disk space usage.

---

### Post by zielstep on 2011-10-05
stephen@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root
                       71G   15G   53G  22% /
none                  1.7G  312K  1.7G   1% /dev
none                  1.7G  1.3M  1.7G   1% /dev/shm
none                  1.7G  208K  1.7G   1% /var/run
none                  1.7G     0  1.7G   0% /var/lock
none                  1.7G     0  1.7G   0% /lib/init/rw
/dev/sda1             228M  201M   16M  93% /boot
/home/stephen/.Private
                       71G   15G   53G  22% /home/stephen

------------------------------------------------
I'm not sure how long the other code is supposed to take, but after 5 minutes this is what I have:
------------------------------------------------
stephen@ubuntu:~$ sudo du -h -c --max-depth=1 /
[sudo] password for stephen: 
4.8G    /usr
4.0K    /cdrom
4.0K    /mnt
7.3M    /sbin
4.0K    /media
6.4M    /bin
950M    /lib
du: cannot access `/proc/2372/task/2372/fd/3': No such file or directory
du: cannot access `/proc/2372/task/2372/fdinfo/3': No such file or directory
du: cannot access `/proc/2372/fd/3': No such file or directory
du: cannot access `/proc/2372/fdinfo/3': No such file or directory
0    /proc
16K    /lost+found
72K    /tmp
4.0K    /opt
463M    /var
du: cannot access `/home/stephen/.gvfs': Permission denied

---

### Post by zielstep on 2011-10-05
Of course, 10 seconds after I posted that, it finishes.  So here is the complete result:

stephen@ubuntu:~$ sudo du -h -c --max-depth=1 /
[sudo] password for stephen: 
4.8G    /usr
4.0K    /cdrom
4.0K    /mnt
7.3M    /sbin
4.0K    /media
6.4M    /bin
950M    /lib
du: cannot access `/proc/2372/task/2372/fd/3': No such file or directory
du: cannot access `/proc/2372/task/2372/fdinfo/3': No such file or directory
du: cannot access `/proc/2372/fd/3': No such file or directory
du: cannot access `/proc/2372/fdinfo/3': No such file or directory
0    /proc
16K    /lost+found
72K    /tmp
4.0K    /opt
463M    /var
du: cannot access `/home/stephen/.gvfs': Permission denied
16G    /home
4.0K    /selinux
16M    /etc
1.6M    /dev
0    /sys
200K    /srv
201M    /boot
404K    /root
22G    /
22G    total

---

### Post by Rasa1111 on 2011-10-05
you can try ```
sudo apt-get autoclean
```in terminal.
See how much space that frees up.


You can also use ubuntu tweak to clean up old package caches, old kernels, old debs, etc.
Those things can take up a bit of space after awhile.

There are other ways to do the same things, but Tweak makes it very easy.

Good luck.

---

### Post by kuchera68 on 2011-10-05
Unless I am missing something, it appears that the only partition that is even remotely full is your boot partition. The only thing that comes to mind is the point under 6a. -> Kernel Installation Failure in the post [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)[B]. 

[/B]It mentions that a separate boot partition and too many older kernel installations could give the too little disk space error. Either follow the recommendations within this post, or better yet see if zielstep's recommendation frees up some space for you.

---

### Post by zielstep on 2011-10-08
Thank you.  For those who see this thread in the future, the link to the other thread solved my problem.  In summary, here is what you do:

Go to terminal, type "uname -a" without the quotes.  This will get you the version of the kernal that you are running.  Even if you try to delete that version, Ubuntu will not let you.

Go to Synaptic Package Manager and delete all of the other kernals you have installed except 1.  You don't delete one of them (in addition to the one you are running, which you cannot delete anyway) because if anything goes wrong, you can use that other "latest" copy.  I couldn't find any instances of people having problems where they needed that other kernal online, however, but I suppose it *might* happen.  So think of this as insurance :).

After you remove all of the older kernals, you will free up a ton of space.  I freed up almost a GB of space on my HD.  Do this periodically, and you will not have any problems.

---

