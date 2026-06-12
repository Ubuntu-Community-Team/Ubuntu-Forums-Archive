---
title: "accidentally chmod 600  -R on everything"
date: 2011-04-30
forum: General Help
---

### Post by ethego on 2011-04-30
hello, i'm new
i was in the middle of trying to recover the "*chmod 777 everything*" incident which cause breakdown on myriad of services on my lucid ubuntu server. unfortunately one malpractice leads to another disaster. as the title suggests, i accidentally *chmod 600 -R on "/"* (should have been /etc but i pressed *enter* prematurely, bummer) now everything is DENIED even for the root user! i can't even relog via ssh since the root password is also denied.

i still keep that last ssh login open since i don't know what else i can do.
any command i typed will just output something like:
root@server /# ls
-bash: /bin/ls: Permission denied
-bash: /bin/pwd: Permission denied
-bash: /bin/pwd: Permission denied
-bash: /bin/grep: Permission denied
-bash: /usr/bin/dirname: Permission denied
-bash: /usr/bin/dirname: Permission denied
-bash: [: =: unary operator expected
-bash: /usr/bin/basename: Permission denied
-bash: /usr/bin/basename: Permission denied
root@server /# chmod 755 -R /
-bash: /bin/chmod: Permission denied
-bash: /bin/pwd: Permission denied
-bash: /bin/pwd: Permission denied
-bash: /bin/grep: Permission denied
-bash: /usr/bin/dirname: Permission denied
-bash: /usr/bin/dirname: Permission denied
-bash: [: =: unary operator expected
-bash: /usr/bin/basename: Permission denied
-bash: /usr/bin/basename: Permission denied

please, any suggestion will be greatly appreciated. thank you

---

### Post by mpace965 on 2011-04-30
This is probably the last thing you want to hear but you might just need a fresh install of Ubuntu.

---

### Post by wojox on 2011-04-30
Back up everything you need in /home from a live-cd and accidentally reinstall. :P

---

### Post by |{urse on 2011-04-30
Yeah, theres a couple ridiculous things you could do but it's going to be easier to reinstall.

---

### Post by ethego on 2011-04-30
omg, i knew it](*,)i'm screwed
oh well, thank you for the quick replies, guys!
i hope nobody follow my stupid steps

cheers

---

### Post by kiyop on 2011-04-30
I think #3 and #4 are right.

But if you dare to try to recover ....

Boot with Ubuntu Live CD and enter into terminal and type
```
sudo su
```Mount the partition by the command "mount" with option "-o rw" and change permissions by the command "chmod".
I think you know the detail of "mount" and "chmod".
```
man mount
man chmod
```In my ubuntu 11.04, 
```
# ls / -la
```gives:
> drwxr-xr-x  22 root root  4096 2011-04-29 02:43 .
drwxr-xr-x  22 root root  4096 2011-04-29 02:43 ..
drwxr-xr-x   2 root root  4096 2011-04-29 02:51 bin
drwxr-xr-x   3 root root  4096 2011-04-30 13:20 boot
drwxr-xr-x   2 root root  4096 2011-04-29 02:33 cdrom
drwxr-xr-x  18 root root  5180 2011-05-01 10:20 dev
drwxr-xr-x 149 root root 12288 2011-05-01 10:20 etc
drwxr-xr-x   3 root root  4096 2011-04-29 02:35 home
lrwxrwxrwx   1 root root    32 2011-04-29 02:43 initrd.img -> boot/initrd.img-2.6.38-8-generic
drwxr-xr-x  19 root root  4096 2011-04-29 02:51 lib
drwx------   2 root root 16384 2011-04-29 02:24 lost+found
drwxr-xr-x  11 root root  4096 2011-05-01 10:20 media
drwxr-xr-x   2 root root  4096 2011-04-22 01:50 mnt
drwxr-xr-x   2 root root  4096 2011-04-26 07:50 opt
dr-xr-xr-x 162 root root     0 2011-05-01 10:19 proc
drwx------   5 root root  4096 2011-05-01 03:01 root
drwxr-xr-x   2 root root  4096 2011-04-29 11:36 sbin
drwxr-xr-x   2 root root  4096 2011-03-21 17:26 selinux
drwxr-xr-x   2 root root  4096 2011-04-26 07:50 srv
drwxr-xr-x  12 root root     0 2011-05-01 10:19 sys
drwxrwxrwt  16 root root  4096 2011-05-01 12:17 tmp
drwxr-xr-x  11 root root  4096 2011-04-26 07:56 usr
drwxr-xr-x  14 root root  4096 2011-04-29 18:58 var
lrwxrwxrwx   1 root root    29 2011-04-29 02:43 vmlinuz -> boot/vmlinuz-2.6.38-8-generic

---

