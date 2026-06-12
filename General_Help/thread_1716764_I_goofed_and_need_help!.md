---
title: "I goofed and need help!"
date: 2011-03-28
forum: General Help
---

### Post by tamccullough on 2011-03-28
Hi.

1. I was trying to compile a new version of blender from source.

2. It wasn't working. Apparently it is using python 3.2 now.

3. So I grabbed the source of python 3.2, compiled and installed. I think.

4. Still wouldn't compile. Couldn't find python 3.2.

5. So I went in to usr/share/python and changed debian-defaults to use 3.2 as the default.

6. To do that I made myself the owner of the usr directory

7. Now my system is buggered.

8. How do I restore roots privileges (if thats the problem)?

Thanks!

---

### Post by tamccullough on 2011-03-29
*bump*

---

### Post by 3Miro on 2011-03-29
Post the result from:
```
ls -al /usr/
```

---

### Post by tamccullough on 2011-03-29
Hi, here it is.
```
total 432
drwxrwxr-x  11 todd root   4096 2010-10-18 16:20 .
drwxr-xr-x  24 root root   4096 2011-03-03 21:33 ..
drwxrwxr-x   2 todd root  69632 2011-03-28 22:46 bin
drwxrwxr-x   2 todd root   4096 2011-03-06 13:46 games
drwxrwxr-x 187 todd root  69632 2011-03-15 22:46 include
drwxrwxr-x 284 todd root 126976 2011-03-27 10:39 lib
drwxrwxr-x  48 todd root 118784 2011-03-23 08:36 lib32
lrwxrwxrwx   1 todd root      3 2010-10-18 15:47 lib64 -> lib
drwxrwxr-x  10 todd root   4096 2010-10-07 11:56 local
drwxrwxr-x   2 todd root  12288 2011-03-23 08:37 sbin
drwxrwxr-x 414 todd root  12288 2011-03-07 23:09 share
drwxrwxr-x  17 todd src    4096 2011-03-03 21:33 src
```

---

### Post by bodhi.zazen on 2011-03-29
> **tamccullough said:**
> Hi, here it is.
```
total 432
drwxrwxr-x  11 todd root   4096 2010-10-18 16:20 .
drwxr-xr-x  24 root root   4096 2011-03-03 21:33 ..
drwxrwxr-x   2 todd root  69632 2011-03-28 22:46 bin
drwxrwxr-x   2 todd root   4096 2011-03-06 13:46 games
drwxrwxr-x 187 todd root  69632 2011-03-15 22:46 include
drwxrwxr-x 284 todd root 126976 2011-03-27 10:39 lib
drwxrwxr-x  48 todd root 118784 2011-03-23 08:36 lib32
lrwxrwxrwx   1 todd root      3 2010-10-18 15:47 lib64 -> lib
drwxrwxr-x  10 todd root   4096 2010-10-07 11:56 local
drwxrwxr-x   2 todd root  12288 2011-03-23 08:37 sbin
drwxrwxr-x 414 todd root  12288 2011-03-07 23:09 share
drwxrwxr-x  17 todd src    4096 2011-03-03 21:33 src
```

IMO the easiest way to fix your system is to re-install.

You should not be changing ownership / permissions of anything outside of your home directory.

I highly suggest you review Linux permissions. To edit system files, use sudo.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

do not change ownership / permissions of system files as an excuse to not learn how permissions work.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Learn to use the root account properly in Ubuntu ( sudo / gksu )

With all that said, you might be able to fix your system by changing ownership back to root, you would need to do this with a live CD if you do not have root access.

Mount your install at /mnt

Then change ownership of all those directories back to root.

If you changed all the subdirectories, I would re install. I have seen many people try to manually fix permissions, it takes a long time. I have only seen one success, and I do not know if it was a long term success or only a temporary fix.

---

### Post by 3Miro on 2011-03-29
Most things in /usr should belong to root and
```
sudo chown -R root:root /usr/
```
should do that, however, this will make everything belonging to root and this is probably wrong. Reinstall may be the only viable option here.

You should be careful when copy/paste commands, tricky settings like Python assume that the user knows something about the system and are not always "fool-proof".

---

### Post by tamccullough on 2011-03-29
> **3Miro said:**
> Most things in /usr should belong to root and
```
sudo chown -R root:root /usr/
```should do that, however, this will make everything belonging to root and this is probably wrong. Reinstall may be the only viable option here.

You should be careful when copy/paste commands, tricky settings like Python assume that the user knows something about the system and are not always "fool-proof".

;)

Yep. I've definitely proven that.

---

