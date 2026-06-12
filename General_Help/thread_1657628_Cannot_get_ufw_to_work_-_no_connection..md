---
title: "Cannot get ufw to work - no connection."
date: 2011-01-01
forum: General Help
---

### Post by zozza on 2011-01-01
Hello, 

I am trying to setup ufw and have the following situation. 

I start with ufw disabled.


sudo ufw enable
WARN: uid is 0 but '/' is owned by 1000
ERROR: problem running ufw-init

I now check with sudo ufw status:

WARN: uid is 0 but '/' is owned by 1000
Status: active

At this point I cannot use any internet features and have to do sudo ufw disable.

I check again using sudo ufw status and get:

WARN: uid is 0 but '/' is owned by 1000
Status: inactive

Now internet works.  How can I setup ufw to be on, be able to use the internet, and not get these error messages (whether or not they are related to having no connectivity when ufw is on). 

Thanks.

EDIT: in terms of ownership the id command shows that my username is 1000.  /etc/ and therefore /etc/ufw is owned by root.  I don't understand why / is owned by me rather than by root. 

ls -l / shows:

ls -l /
total 124
drwxr-xr-x   2 root     root      4096 2010-11-25 15:43 bin
drwxr-xr-x   3 root     root      4096 2010-12-30 17:15 boot
drwxr-xr-x   2 root     root      4096 2010-08-08 20:14 cdrom
drwxr-xr-x  18 root     root      3660 2011-01-01 12:20 dev
drwxr-xr-x 146 root     root     36864 2011-01-01 16:39 etc
drwxr-xr-x   3 root     root      4096 2010-08-08 20:16 home
lrwxrwxrwx   1 root     root        33 2010-12-30 17:13 initrd.img -> boot/initrd.img-2.6.32-27-generic
lrwxrwxrwx   1 root     root        33 2010-11-30 08:50 initrd.img.old -> boot/initrd.img-2.6.32-26-generic
drwxr-xr-x  20 root     root     12288 2010-12-30 17:11 lib
drwx------   2 root     root     16384 2010-08-08 20:10 lost+found
drwxr-xr-x   4 username username  4096 2011-01-01 12:20 media
drwxr-xr-x   2 root     root      4096 2010-04-23 11:11 mnt
drwxr-xr-x   2 root     root      4096 2010-04-29 13:17 opt
dr-xr-xr-x 156 root     root         0 2011-01-01 11:37 proc
drwx------  11 root     root      4096 2010-12-31 15:50 root
drwxr-xr-x   2 root     root      4096 2010-12-30 17:14 sbin
drwxr-xr-x   2 root     root      4096 2009-12-05 21:55 selinux
drwxr-xr-x   2 root     root      4096 2010-04-29 13:17 srv
drwxr-xr-x  12 root     root         0 2011-01-01 11:37 sys
drwxr-xr-x  12 root     root      4096 2010-08-03 01:47 thunderbird
drwxrwxrwt  14 root     root      4096 2011-01-01 17:08 tmp
drwxr-xr-x  10 root     root      4096 2010-04-29 13:17 usr
drwxr-xr-x  15 root     root      4096 2010-04-29 13:26 var
lrwxrwxrwx   1 root     root        30 2010-12-30 17:13 vmlinuz -> boot/vmlinuz-2.6.32-27-generic
lrwxrwxrwx   1 root     root        30 2010-11-30 08:50 vmlinuz.old -> boot/vmlinuz-2.6.32-26-generic

---

