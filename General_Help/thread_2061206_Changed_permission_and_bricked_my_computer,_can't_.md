---
title: "Changed permission and bricked my computer, can't even reboot"
date: 2012-09-21
forum: General Help
---

### Post by zachsmthsn on 2012-09-21
I was trying to install a copy of windows 7 on another hard drive using an iso and mounting it as a bootable flash. When I mounted the iso to the flash drive it gave a warning that the flash drive was read only. Using my VAST (not really...) knowledge of ubuntu, I opened that folder in terminal and typed in something along the lines of

sudo chmod 754 /

assuming that I would be pointing to my current directory. (might not have been exactly this, but the issue remains that my permissions are royally screwed up.

It immediately exited me out of my browser and changes all image icons to either blank file icons or red X's. Any folder I tried to open I got "you do not have permission to access ' ' " Yeh... bad things. I tried then going and changing my user to guest just to see what happened, but then my screen went black. 

I rebooted and got an error saying something along the line of
the disk drive UID <long has string> is not ready yet or not present.

Basically, I would like to know if/how to fix it. I had a liveCD at some point and lost it. What I'm thinking now is...

-get a live cd
-Get this iso of windows made into an executable flash drive and try to recover all files from there, then reinstalling ubuntu fresh and starting over. 
-getting a very large hammer and fixing my issues permanently


My biggest concerns: keeping the files on my hard drive through an install of ubuntu (I have most everything backed up, but I just took all my school stuff off of my flash drive and put it in ubuntu so I could use my biggest flash drive to install windows, so some VERY important stuff is not backed up) 
being able to see everything on there if I view it through a windows computer (I'm not sure what it is formatted as, it was a blank Seagate drive before ubuntu was put on it, and I'm not sure if ubuntu reformats a drive before installing or what. 

I'm really in a crunch here, guys, and need to have this fixed as soon as possible. Or at least have my files off of it and run on my laptop for awhile. Any help in this matter would be great.

Thank you all very much

---

### Post by oldfred on 2012-09-22
You really need liveCD. 

You need to backup everything you can first. Normally any changes to permissions in the system, corrupt it and make it about impossible to recover from Clean install is usually best to resolve it.

But if you only did / (root) you may be able to set those back. Fortunately you did not include the R for recursion and change the entire system.

I will post a screen shot of my / so you can see permissions. You just about have to set each separately. Someone may know a better command. Most of the directories have to 755.

I found this in my notes, but I am no expert on permissions and chmod. I have to read book or find some post with more detail.

sudo chmod a+rwX,o-w /
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

Note that if you are using liveCD you have to mount you / so above command will not be / but /media/whereyoumountit ?

See also 
man chmod

Edit:
I booted my liveUSB. I know when I use flash drive my Precise install is in sde3:

```
ubuntu@ubuntu:~$ sudo mkdir /media/precise
ubuntu@ubuntu:~$ sudo mount /dev/sde3 /media/precise
ubuntu@ubuntu:~$ cd /media/precise
ubuntu@ubuntu:/media/precise$ ls -l
total 116
drwxr-xr-x   2 root root  4096 Sep 21 14:18 bin
drwxr-xr-x   3 root root  4096 Sep 11 13:16 boot
drwxr-xr-x   2 root root  4096 Nov  8  2011 cdrom
drwxr-xr-x   5 root root  4096 Nov  7  2011 dev
drwxr-xr-x 166 root root 12288 Sep 22 04:25 etc
drwxr-xr-x   3 root root  4096 Nov  8  2011 home
lrwxrwxrwx   1 root root    33 Sep  8 14:35 initrd.img -> /boot/initrd.img-3.2.0-31-generic
lrwxrwxrwx   1 root root    33 Aug 21 13:52 initrd.img.old -> /boot/initrd.img-3.2.0-30-generic
drwxr-xr-x  25 root root  4096 Sep 13 13:22 lib
drwxr-xr-x   2 root root  4096 Sep 13 13:22 lib64
drwx------   2 root root 16384 Nov  8  2011 lost+found
drwxr-xr-x   4 root root  4096 Sep 22 04:23 media
drwxr-xr-x   9 root root  4096 Sep 19 17:26 mnt
drwxr-xr-x   2 root root  4096 Nov  7  2011 opt
drwxr-xr-x   2 root root  4096 Oct 25  2011 proc
drwx------  13 root root  4096 Sep 19 19:18 root
drwxr-xr-x   7 root root  4096 Nov  7  2011 run
drwxr-xr-x   2 root root 12288 Sep 19 13:24 sbin
drwxr-xr-x   2 root root  4096 Oct 17  2011 selinux
drwxr-xr-x   2 root root  4096 Nov  7  2011 srv
drwxr-xr-x   2 root root  4096 Jul 14  2011 sys
drwxrwxrwt  11 root root  4096 Sep 22 04:25 tmp
drwxr-xr-x  11 root root  4096 Nov  8  2011 usr
drwxr-xr-x  14 root root  4096 Sep 22 04:25 var
lrwxrwxrwx   1 root root    29 Sep  8 14:35 vmlinuz -> boot/vmlinuz-3.2.0-31-generic
lrwxrwxrwx   1 root root    29 Aug 21 13:52 vmlinuz.old -> boot/vmlinuz-3.2.0-30-generic

```So if I mounted it correctly this should change most of the permissions. The others you have to do one at a time.

sudo chmod a+rwX,o-w /media/precise

---

