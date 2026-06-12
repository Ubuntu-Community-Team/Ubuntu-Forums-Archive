---
title: "Home Folder disappear when connected to netwrok"
date: 2010-05-28
forum: General Help
---

### Post by milinddev on 2010-05-28
I recently upgraded to ubuntu10.04 LTS via update manager. Previous version was 10.04 beta. 

After upgrading I am facing very strange problem.
1) If I start my laptop with network connection then all the folder under /home get disappear. When I do ls -l /home it says no folder found.
As all the folder under home is disappearing  it is giving so many errors when I login and as a result of this I am not able to start the gnome UI.

I tried to mkdir under home and it says cannot create directory.
I tried with root login but same error.

2) But it if I start my laptop without any network connection  then I am able to see all the folders under /home and able to login successfully without any error.

I tried to mkdir under home and it was successfully.

3) I also tried this option, first start the laptop without any network connection and login successfully ( Able to see all folder under /home) but as soon as I plug the network cable and once it is connected all folder under  /home disappear and system starts failing.

So if any body can help me to recover that user it will be great as I am having that user since ubuntu8.04 and lots of data and customization is there.

My previous 10.04 beta version was working perfectly.

Thanks,
--milind

---

### Post by lmarmisa on 2010-05-28
Hi milind,

your problem sounds really strange.

Type theses commands in both cases:

> 
[B]df
ls -l /
ls -l /home
echo $HOME[/B]
It would be nice it you could send us the outputs of theses commands.

Best regards,

Luis

---

### Post by milinddev on 2010-05-28
lmarmisa,

Here are the details:

milind@milind-laptop:~$ df
Filesystem           1k-blocks      Used Available Use% Mounted on
/dev/sda5             25588888  18211400   6087872  75% /
none                   1025812       324   1025488   1% /dev
none                   1030028      1272   1028756   1% /dev/shm
none                   1030028       116   1029912   1% /var/run
none                   1030028         0   1030028   0% /var/lock
none                   1030028         0   1030028   0% /lib/init/rw
/dev/sda1             51199120  48728376   2470744  96% /media/disk

milind@milind-laptop:~$ ls -l /
total 29120
drwxr-xr-x    2 root     root         4096 May 25 16:11 bin
drwxr-xr-x    3 root     root         4096 May 25 17:23 boot
lrwxrwxrwx    1 root     root           11 Feb 19  2009 cdrom -> media/cdrom
drwxr-xr-x    3 milind   root         4096 Mar  3  2009 cm
-rw-------    1 root     root       487424 Jan 14 11:36 core
drwxr-xr-x   16 root     root         3780 May 28 12:25 dev
drwxr-xr-x  171 root     root        12288 May 28 12:25 etc
drwxr-xr-x    2 root     root            0 May 28 12:25 home
drwxr-xr-x    2 root     root         4096 Apr 22  2008 initrd
lrwxrwxrwx    1 root     root           33 May 25 16:10 initrd.img -> boot/initrd.img-2.6.32-22-generic
lrwxrwxrwx    1 root     root           33 Apr  9 11:36 initrd.img.old -> boot/initrd.img-2.6.31-21-generic
drwxr-xr-x   21 root     root        12288 May 27 11:47 lib
drwx------    2 root     root        16384 Feb 19  2009 lost+found
drwxr-xr-x    4 root     root         4096 May 28 12:25 media
drwxr-xr-x    2 root     root         4096 Apr 15  2008 mnt
drwxr-xr-x    4 root     root         4096 May 26 12:17 myhome
dr-xr-xr-x    3 root     root         4096 May 25 16:42 nfs
drwxr-xr-x    4 root     root         4096 Apr 12 15:40 opt
dr-xr-xr-x  189 root     root            0 May 28  2010 proc
drwxr-xr-x   28 root     root         4096 May 25 18:50 root
drwxr-xr-x    2 root     root         4096 May 27 11:46 sbin
drwxr-xr-x    2 root     root         4096 Mar  6  2009 selinux
drwxr-xr-x    4 root     root         4096 Dec  7 13:25 srv
drwxr-xr-x   12 root     root            0 May 28  2010 sys
drwxrwxrwt   15 root     root     29274112 May 28 12:29 tmp
drwxr-xr-x    2 root     root         4096 Mar 29 10:04 TMP
drwxr-xr-x   14 root     root         4096 Dec 21 16:56 usr
drwxr-xr-x   16 root     root         4096 Mar  3  2009 var
lrwxrwxrwx    1 root     root           30 May 25 16:10 vmlinuz -> boot/vmlinuz-2.6.32-22-generic
lrwxrwxrwx    1 root     root           30 Apr  9 11:36 vmlinuz.old -> boot/vmlinuz-2.6.31-21-generic

milind@milind-laptop:~$ ls -l /home
total 0

milind@milind-laptop:~$ echo $HOME
/home/milind


Thanks,
--milind

---

### Post by lmarmisa on 2010-05-28
This is the case when you are connected to the network. Right?.

The **/home** dir seems empty but there is a directory named **/myhome**. I do not know if this is significant or not. Could you show us the content of this directory?

> 
**ls -l /myhome**
Could you repeat those commands without any network connection?.

You can save the outputs in a temporary file on the /media/disk partition

> 
[B]df > /media/disk/temp.txt
ls -l / >> /media/disk/temp.txt
ls -l /home >> /media/disk/temp.txt
echo $HOME >> /media/disk/temp.txt[/B]
When you plug the cable, you will have access to the outputs of the commands typing

> 
**cat /media/disk/temp.txt**


---

### Post by milinddev on 2010-05-28
Yah I was connected to the netwrok.

Folder myhome is actually home folder for another user which I had created (using adduser) because of previous errors.
New user works perfectly without any error as home folder reside in /myhome and not in /home.

Anyhow the content of /myhome are as below:
total 8
drwxr-xr-x    3 root     root         4096 May 26 12:18 ant
drwxr-xr-x   38 milindao milindao     4096 May 28 16:35 milindaol

Following are the details required by you without connecting to the network:

df

Filesystem           1k-blocks      Used Available Use% Mounted on
/dev/sda5             25588888  18215748   6083524  75% /
none                   1025812       312   1025500   1% /dev
none                   1030028       332   1029696   1% /dev/shm
none                   1030028       108   1029920   1% /var/run
none                   1030028         0   1030028   0% /var/lock
none                   1030028         0   1030028   0% /lib/init/rw
/dev/sda1             51199120  48711336   2487784  96% /media/disk

ls -l / 

total 29124
drwxr-xr-x    2 root     root         4096 May 25 16:11 bin
drwxr-xr-x    3 root     root         4096 May 25 17:23 boot
lrwxrwxrwx    1 root     root           11 Feb 19  2009 cdrom -> media/cdrom
drwxr-xr-x    3 milind   root         4096 Mar  3  2009 cm
-rw-------    1 root     root       487424 Jan 14 11:36 core
drwxr-xr-x   16 root     root         3740 May 29 08:57 dev
drwxr-xr-x  171 root     root        12288 May 29 08:58 etc
drwxr-xr-x    4 root     root         4096 Dec 16 17:10 home
drwxr-xr-x    2 root     root         4096 Apr 22  2008 initrd
lrwxrwxrwx    1 root     root           33 May 25 16:10 initrd.img -> boot/initrd.img-2.6.32-22-generic
lrwxrwxrwx    1 root     root           33 Apr  9 11:36 initrd.img.old -> boot/initrd.img-2.6.31-21-generic
drwxr-xr-x   21 root     root        12288 May 27 11:47 lib
drwx------    2 root     root        16384 Feb 19  2009 lost+found
drwxr-xr-x    4 root     root         4096 May 29 08:58 media
drwxr-xr-x    2 root     root         4096 Apr 15  2008 mnt
drwxr-xr-x    4 root     root         4096 May 26 12:17 myhome
dr-xr-xr-x    3 root     root         4096 May 25 16:42 nfs
drwxr-xr-x    4 root     root         4096 Apr 12 15:40 opt
dr-xr-xr-x  212 root     root            0 May 29  2010 proc
drwxr-xr-x   28 root     root         4096 May 25 18:50 root
drwxr-xr-x    2 root     root         4096 May 27 11:46 sbin
drwxr-xr-x    2 root     root         4096 Mar  6  2009 selinux
drwxr-xr-x    4 root     root         4096 Dec  7 13:25 srv
drwxr-xr-x   12 root     root            0 May 29  2010 sys
drwxrwxrwt   15 root     root     29274112 May 29 08:59 tmp
drwxr-xr-x    2 root     root         4096 Mar 29 10:04 TMP
drwxr-xr-x   14 root     root         4096 Dec 21 16:56 usr
drwxr-xr-x   16 root     root         4096 Mar  3  2009 var
lrwxrwxrwx    1 root     root           30 May 25 16:10 vmlinuz -> boot/vmlinuz-2.6.32-22-generic
lrwxrwxrwx    1 root     root           30 Apr  9 11:36 vmlinuz.old -> boot/vmlinuz-2.6.31-21-generic

ls -l /home

total 16
drwxr-xr-x   49 fortanma fortanma     4096 Apr 10 11:42 fortanmay
drwxr-xr-x  126 milind   milind      12288 May 29 09:01 milind

echo $HOME

/home/milind

If you need more info let me know.

Thanks,
--milind

---

