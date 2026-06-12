---
title: "Can't execute sudo after moving /usr/bin"
date: 2010-08-29
forum: General Help
---

### Post by anandamide on 2010-08-29
Moved /usr/bin to a different partition, now any sudo command results in:

```
sudo: must be setuid root
```

Which I read as meaning that /usr/bin/sudo must be owned by root - and it is:

```
$ ls -l /usr/bin/sudo
-rwxr-xr-x 1 root root 123504 2010-08-19 20:55 /usr/bin/sudo
```

I can get root access through 'su', but obviously this is far from ideal. Hoping this is something simple to sort out, but I'm not too hot on permissions and users / groups. 

Cheers :-)

---

### Post by sisco311 on 2010-08-29
When you cp the files to the new partition, you have to use the **--preserve=all** option. Otherwise the [access right flags]("http://en.wikipedia.org/wiki/Setuid") are cleared:
```
sudo cp -R --preserve=all SOURCE DEST
```

---

### Post by lmarmisa on 2010-08-29
This is the output of the same command in my case:

```

ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 127664 2010-06-18 22:40 /usr/bin/sudo

```

The s flag (set user or group ID on execution) is shown here. Maybe this is the problem.

---

### Post by sisco311 on 2010-08-29
> **lmarmisa said:**
> Maybe this is the problem.


Yes, but sudo is not the only setuid/setgid file in /usr/bin:
```
find /usr/bin/ -perm +6000 -exec ls -al '{}' +;
-rwsr-xr-x 1 root root    40800 May 28 04:17 /usr/bin/chage
-rwsr-xr-x 1 root root    20824 May 28 04:17 /usr/bin/chfn
-rwsr-xr-x 1 root root    20088 May 28 04:17 /usr/bin/chsh
-rwsr-x--- 1 root users   12336 Feb 24  2010 /usr/bin/crontab
-r-sr-xr-x 1 root root   142832 Feb 10  2010 /usr/bin/cu
-rwsr-xr-x 1 root root    15824 May 28 04:17 /usr/bin/expiry
-rwsr-xr-x 1 root root   409551 Jul 12 17:36 /usr/bin/fbterm
-r-xr-sr-x 1 root games  145304 Jun 22 09:57 /usr/bin/glines
-r-xr-sr-x 1 root games  138728 Jun 22 09:57 /usr/bin/gnibbles
-r-xr-sr-x 1 root games  203648 Jun 22 09:57 /usr/bin/gnobots2
-r-xr-sr-x 1 root games  151576 Jun 22 09:57 /usr/bin/gnomine
-r-xr-sr-x 1 root games  133976 Jun 22 09:57 /usr/bin/gnotravex
-r-xr-sr-x 1 root games  135248 Jun 22 09:57 /usr/bin/gnotski
-rwsr-xr-x 1 root root    32624 May 28 04:17 /usr/bin/gpasswd
-r-xr-sr-x 1 root games  107120 Jun 22 09:57 /usr/bin/gtali
-rwsr-xr-x 1 root root    15736 May 27 18:16 /usr/bin/ksu
-r-xr-sr-x 1 root games  117464 Jun 22 09:57 /usr/bin/mahjongg
-rwxr-sr-x 1 root mem     96120 Apr  4  2009 /usr/bin/mail
-rwsr-xr-x 1 root root    21784 May 28 04:17 /usr/bin/newgrp
-rwsr-xr-x 1 root root    11384 May 27 18:16 /usr/bin/otp
-rwsr-xr-x 1 root root    24616 May 28 04:17 /usr/bin/passwd
-rwsr-xr-x 1 root root    17256 Mar 13 21:02 /usr/bin/pkexec
-r-xr-sr-x 1 root games  130440 Jun 22 09:57 /usr/bin/quadrapassel
-rwsr-xr-x 1 root root   354264 May 30  2009 /usr/bin/screen-4.0.3
-rwsr-xr-x 1 root root     9424 May  4 19:01 /usr/bin/slock
---s--x--x 2 root root   192312 Aug 11 05:54 /usr/bin/sudo
---s--x--x 2 root root   192312 Aug 11 05:54 /usr/bin/sudoedit
-r-sr-xr-x 1 root root    97480 Feb 10  2010 /usr/bin/uucp
-r-sr-xr-x 1 root root    37408 Feb 10  2010 /usr/bin/uuname
-r-sr-xr-x 1 root root   109880 Feb 10  2010 /usr/bin/uustat
-r-sr-xr-x 1 root root    97536 Feb 10  2010 /usr/bin/uux
-rwxr-sr-x 1 root tty     10968 Aug  2 17:17 /usr/bin/write
-rwsr-xr-x 1 root root  1913552 Jun 21 15:02 /usr/bin/Xorg

```

---

### Post by lmarmisa on 2010-08-29
> **sisco311 said:**
> Yes, but sudo is not the only setuid/setgid file in /usr/bin:
```
find /usr/bin/ -perm +6000 -exec ls -al '{}' +;
-rwsr-xr-x 1 root root    40800 May 28 04:17 /usr/bin/chage
-rwsr-xr-x 1 root root    20824 May 28 04:17 /usr/bin/chfn
-rwsr-xr-x 1 root root    20088 May 28 04:17 /usr/bin/chsh
-rwsr-x--- 1 root users   12336 Feb 24  2010 /usr/bin/crontab
-r-sr-xr-x 1 root root   142832 Feb 10  2010 /usr/bin/cu
-rwsr-xr-x 1 root root    15824 May 28 04:17 /usr/bin/expiry
-rwsr-xr-x 1 root root   409551 Jul 12 17:36 /usr/bin/fbterm
-r-xr-sr-x 1 root games  145304 Jun 22 09:57 /usr/bin/glines
-r-xr-sr-x 1 root games  138728 Jun 22 09:57 /usr/bin/gnibbles
-r-xr-sr-x 1 root games  203648 Jun 22 09:57 /usr/bin/gnobots2
-r-xr-sr-x 1 root games  151576 Jun 22 09:57 /usr/bin/gnomine
-r-xr-sr-x 1 root games  133976 Jun 22 09:57 /usr/bin/gnotravex
-r-xr-sr-x 1 root games  135248 Jun 22 09:57 /usr/bin/gnotski
-rwsr-xr-x 1 root root    32624 May 28 04:17 /usr/bin/gpasswd
-r-xr-sr-x 1 root games  107120 Jun 22 09:57 /usr/bin/gtali
-rwsr-xr-x 1 root root    15736 May 27 18:16 /usr/bin/ksu
-r-xr-sr-x 1 root games  117464 Jun 22 09:57 /usr/bin/mahjongg
-rwxr-sr-x 1 root mem     96120 Apr  4  2009 /usr/bin/mail
-rwsr-xr-x 1 root root    21784 May 28 04:17 /usr/bin/newgrp
-rwsr-xr-x 1 root root    11384 May 27 18:16 /usr/bin/otp
-rwsr-xr-x 1 root root    24616 May 28 04:17 /usr/bin/passwd
-rwsr-xr-x 1 root root    17256 Mar 13 21:02 /usr/bin/pkexec
-r-xr-sr-x 1 root games  130440 Jun 22 09:57 /usr/bin/quadrapassel
-rwsr-xr-x 1 root root   354264 May 30  2009 /usr/bin/screen-4.0.3
-rwsr-xr-x 1 root root     9424 May  4 19:01 /usr/bin/slock
---s--x--x 2 root root   192312 Aug 11 05:54 /usr/bin/sudo
---s--x--x 2 root root   192312 Aug 11 05:54 /usr/bin/sudoedit
-r-sr-xr-x 1 root root    97480 Feb 10  2010 /usr/bin/uucp
-r-sr-xr-x 1 root root    37408 Feb 10  2010 /usr/bin/uuname
-r-sr-xr-x 1 root root   109880 Feb 10  2010 /usr/bin/uustat
-r-sr-xr-x 1 root root    97536 Feb 10  2010 /usr/bin/uux
-rwxr-sr-x 1 root tty     10968 Aug  2 17:17 /usr/bin/write
-rwsr-xr-x 1 root root  1913552 Jun 21 15:02 /usr/bin/Xorg

```

I agree, but the specific problem of **sudo** can be easily solved running the command **chmod **from the root account (**su**).

---

### Post by anandamide on 2010-08-29
Thanks for the reply :-). I still have /usr/bin-old so the fix won't be too daunting.

Thanks

---

### Post by john newbuntu on 2010-08-29
Yeah should have used the preserve all if you hadn't used it.  Try "chmod u+s /usr/bin/sudo" as root and see if that helps.
Might have to do this to a few more files. or use chmod 4755 sudo

---

