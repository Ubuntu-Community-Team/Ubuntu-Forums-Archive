---
title: "Changing ownership of /usr/bin/sudo"
date: 2011-09-30
forum: General Help
---

### Post by andrewyu on 2011-09-30
While in the directory /usr/bin, I STUPIDLY  ran the command 

$ sudo chown -R mysql .

Now all of my binaries in the directory are owned by mysql for example 

$ ls -l /usr/bin/sudo
-rwxr-xr-x 2 mysql root 168800 2011-05-29 20:06 /usr/bin/sudo

More importantly, whenever I run anything with sudo I get the error 

sudo: must be setuid root

Now is it possible for root to get back ownership of sudo?   Or what are my other options?

---

### Post by yetiman64 on 2011-09-30
You can repair the permissions  for /usr/bin/sudo from a terminal off a live cd.

Boot up a live cd (select the "Try Ubuntu" option) and go to Places menu and mount the root partition of your install by clicking it.

Locate the root filesystem of your instal in /media.

Open a terminal and use the command,

```
sudo chown root:root /media/<UUID_or_Label-of-your-installs-root-partition>/usr/bin/sudo
```Replace <UUID_or_Label-of-your-installs-root-partition> with the actual UUID or Volume Label the root partition is mounted as.

Note a password is not required for sudo when operating off the live cd.

Reboot back into your install and check if sudo works ok now. Once sudo is fixed you should be able to repair any other changes locally from the installation itself. Good luck.

---

### Post by dcstar on 2011-09-30
> **yetiman64 said:**
> You can repair the permissions  for /usr/bin/sudo from a terminal off a live cd.

Boot up a live cd and go to Places menu and mount the root partition of your install by clicking it.

Locate the root filesystem of your intall in /media.

Open a terminal and use the command,

```
sudo chown root:root /media/<UUID_or_Label-of-your-installs-root-partition>/usr/bin/sudo
```Replace <UUID_or_Label-of-your-installs-root-partition> with the actual UUID or Volume Label the root partition is mounted as.
.......

The root **UID** is 0 on Ubuntu systems.

UUID is what Partitions have.

---

### Post by yetiman64 on 2011-09-30
> **dcstar said:**
> The root **UID** is 0 on Ubuntu systems.

UUID is what Partitions have.
And if the root filesystem of the install does not have a Label it will be mounted under /media with the UUID of the root filesystem. I am not referring to the User ID of root but the UUID of the root filesystem.

So > UUID is what Partitions haveis what I am obviously referring to.

---

### Post by CatKiller on 2011-09-30
> **dcstar said:**
> The root **UID** is 0 on Ubuntu systems.

UUID is what Partitions have.

I'm not sure what your point is. Yetiman's talking about partitions, not users.

---

### Post by andrewyu on 2011-09-30
Thanks for the responses.  I followed the steps and once I rebooted from hard disk the ownership of sudo is ownership back to root:

$ ls -l /usr/bin/sudo
-rwxr-xr-x 2 root root 168800 2011-05-29 20:06 /usr/bin/sudo

However I am still not able to use sudo: 

andrew@dell-xps:/usr/bin$ sudo chown root:root man
sudo: must be setuid root

Are there any additional steps I can try?

---

### Post by yetiman64 on 2011-09-30
> **andrewyu said:**
> Thanks for the responses.  I followed the steps and once I rebooted from hard disk the ownership of sudo is ownership back to root:

$ ls -l /usr/bin/sudo
-rwxr-xr-x 2 root root 168800 2011-05-29 20:06 /usr/bin/sudo

However I am still not able to use sudo: 

andrew@dell-xps:/usr/bin$ sudo chown root:root man
sudo: must be setuid root

Are there any additional steps I can try?
Ah I focused on the ownership only, missed the setuid
From the live cd (same process as before) use the command ```
sudo chmod u+s /media/<UUID_or_Label-of-your-installs-root-partition>/usr/bin/sudo
```That should set sudo back to -rw**s**r-xr-x. This is what sudo shows on this install.

Full permissions / ownership for sudo here,

```
-rwsr-xr-x 2 root root 168800 2011-05-30 16:06 /usr/bin/sudo
```

---

### Post by andrewyu on 2011-10-03
Thanks, this gave root ownership of sudo.  This was a huge help.

---

### Post by The Cog on 2011-10-03
There are a few other programs in /usr/bin that should not be root root ownership, or that should be setuid. To be really sure, I think you should reinstall. But if you prefer to try to fix by hand, here is a list of the non-standard files in my bin:
```
$ ls -l /usr/bin | grep -v '^-rwxr-xr-x 1 root   root' | grep -v 'lrwxrwxrwx 1 root   root'
total 218200
-rwsr-xr-x 1 root   root       13804 2010-11-15 08:08 arping
-rwsr-sr-x 1 daemon daemon     42752 2010-06-27 20:36 at
-rwxr-sr-x 1 root   tty         9672 2011-02-01 13:58 bsd-write
-rwxr-xr-x 2 root   root       36601 2011-04-26 17:20 c2ph
-rwxr-sr-x 1 root   shadow     45228 2011-02-21 00:16 chage
-rwsr-xr-x 1 root   root       36140 2011-02-21 00:16 chfn
-rwsr-xr-x 1 root   root       31692 2011-02-21 00:16 chsh
-rwxr-sr-x 1 root   crontab    30624 2011-01-05 10:22 crontab
-rwxr-sr-x 1 root   mail       13840 2010-05-18 16:08 dotlockfile
-rwxr-sr-x 1 root   shadow     18064 2011-02-21 00:16 expiry
-rwsr-xr-x 1 root   root       53804 2011-02-21 00:16 gpasswd
-rwxr-xr-x 4 root   root        9672 2010-06-22 18:36 lockfile-check
-rwxr-xr-x 4 root   root        9672 2010-06-22 18:36 lockfile-create
-rwxr-xr-x 4 root   root        9672 2010-06-22 18:36 lockfile-remove
-rwxr-xr-x 4 root   root        9672 2010-06-22 18:36 lockfile-touch
-rwsr-xr-x 1 root   lpadmin     9404 2011-09-12 15:46 lppasswd
-rwxr-sr-x 3 root   mail        9668 2010-06-22 18:36 mail-lock
-rwxr-sr-x 3 root   mail        9668 2010-06-22 18:36 mail-touchlock
-rwxr-sr-x 3 root   mail        9668 2010-06-22 18:36 mail-unlock
-rwxr-sr-x 1 root   mlocate    30276 2010-10-15 01:24 mlocate
-rwsr-xr-x 1 root   root       52048 2010-10-15 16:36 mtr
-rwsr-xr-x 1 root   root       26744 2011-02-21 00:16 newgrp
-rwsr-xr-x 1 root   root       37132 2011-02-21 00:16 passwd
-rwxr-xr-x 2 root   root     1220276 2011-04-26 17:21 perl
-rwxr-xr-x 2 root   root     1220276 2011-04-26 17:21 perl5.10.1
-rwxr-xr-x 2 root   root       53317 2011-04-26 17:20 perlbug
-rwxr-xr-x 2 root   root       53317 2011-04-26 17:20 perlthanks
-rwsr-xr-x 1 root   root       18032 2011-04-19 23:56 pkexec
-rwxr-xr-x 2 root   root       53325 2011-04-26 17:20 psed
-rwxr-xr-x 2 root   root       36601 2011-04-26 17:20 pstruct
-rwxr-xr-x 2 root   root       53325 2011-04-26 17:20 s2p
-rwxr-sr-x 1 root   ssh       112032 2011-04-02 11:16 ssh-agent
-rwsr-xr-x 2 root   root      144508 2011-05-30 06:51 sudo
-rwsr-xr-x 2 root   root      144508 2011-05-30 06:51 sudoedit
-rwsr-xr-x 1 root   root       13944 2010-11-15 08:08 traceroute6.iputils
-rwxr-xr-x 2 root   root      153236 2011-01-28 09:44 unzip
-rwxr-sr-x 1 root   tty         9728 2011-03-21 08:28 wall
-rwsr-sr-x 1 root   root        9628 2011-05-18 06:15 X
-rwxr-xr-x 2 root   root      153236 2011-01-28 09:44 zipinfo

```

---

### Post by yetiman64 on 2011-10-03
> **The Cog said:**
> ...
OP pay particular attention to this post if you are manually resetting permissions for more than just sudo in /usr/bin.

In fact I would tend to agree, in your situation, with 
> To be really sure, I think you should reinstall.That is the safest option to avoid future/further problems. Fixing permissions from a live cd is good to know how to do, its usefulness though is really dependent on the extent of damage your command has done.

Check all in that location against The Cog's code box list very carefully if you decide to go the manual path.
> Thanks, this gave root ownership of sudo.  This was a huge help. You're most welcome. :) Also if you are happy with the end result (no more problems) please mark your thread as solved, link #5 in my sig has instructions if needed. 

Cheers from yetiman64.

---

