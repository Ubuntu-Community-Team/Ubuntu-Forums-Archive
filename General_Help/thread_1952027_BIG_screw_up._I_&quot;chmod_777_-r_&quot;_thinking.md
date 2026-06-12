---
title: "BIG screw up. I &quot;chmod 777 -r /&quot; thinking I would give permissions to all my files"
date: 2012-04-03
forum: General Help
---

### Post by kroeze on 2012-04-03
So I was trying to get permission to all my files so I could install and delete things easier, but when I ran 
```
sudo chmod 777 -r  / 
```I lost all sudo power. So now I can't do anything essentially. I was wondering if there was an easy way to fix this (very doubtful), and if not, is it possible to install ubuntu on a different partition, and then access my files on this partition i.e. saving my files. 

When I run

```
 fdisk -l
```I don't get an output. And when I run 

```
mount 
```I get

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,sosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
non on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

Any help would be greatly appreciated! As well I do know I screwed up and should not be chmod 777ing directories, especially /.

---

### Post by CharlesA on 2012-04-03
Did you use a -R or -r?

If you just used -r, you should be ok to boot from a cd and restore permissions to /

---

### Post by jerome1232 on 2012-04-03
--snip--

---

### Post by jerome1232 on 2012-04-03
eh, huh? -r and -R mean the same thing
```
             -R, --recursive
              change files and directories recursively


```

---

### Post by CharlesA on 2012-04-03
Ah. I must have been looking at an old man page.

Best thing to do is back up your data from a livecd and reinstall in this case.

---

### Post by kroeze on 2012-04-03
I used -r. 

So would I be able to do this just through running ubuntu from the cd and changing permissions, or would I have to install on a different partition and then change permissions?

Also, how would I go about changing permission back to how they were originally?

---

### Post by QIII on 2012-04-03
Changing permissions back would take you a month of Sundays and you would have to know exactly what you needed to change.

Back up your important data (ie.: /home) and reinstall.

Important lesson here:  Just a dab of recursion goes a long way.

---

### Post by RJARRRPCGP on 2012-04-03
If that's allowing everything, I can't see why it would revoke your sudo permission!

The only possible thing I can see is that you took away execute for the binaries!

Doing "777" to all the binaries appears to be a fatal mistake, because of **-x** not being preserved!

That's likely why it won't let you sudo anymore!

---

### Post by CharlesA on 2012-04-03
if /etc/sudoers has the wrong permissions it won't work.

---

### Post by kroeze on 2012-04-03
When I try to copy my /home directory to my external hard drive, I'm denied because I don't have permissions to read it. Also I'm not exactly sure how to access my other hard drive since when I run the cd it's viewed at a different device. Any thoughts on how to backup my /home on my external hard drive?

---

### Post by CharlesA on 2012-04-03
Boot off a livecd, open a terminal and just copy the files with sudo:

```
sudo rsync -ai /home/ /path/to/external/directory/
```

---

### Post by kroeze on 2012-04-03
Thank you so much! I had to run:

```
sudo rsync -ai /media/myharddrive/home/ /path/to/external/directory/
```

but it's all currently being copied over right now. I'll reinstall Ubuntu and never play with something I don't know about for a little while at least. haha

---

### Post by CharlesA on 2012-04-03
You had your home folder on a separate hard drive?

EDIT: Nevermind, I'm an idiot. :roll:

Hopefully the copy goes smoothly.

---

### Post by iponeverything on 2012-04-03
> **kroeze said:**
> Thank you so much! I had to run:

```
sudo rsync -ai /media/myharddrive/home/ /path/to/external/directory/
```

but it's all currently being copied over right now. I'll reinstall Ubuntu and never play with something I don't know about for a little while at least. haha

It might sound strange.. but

Generally, messing things up on your system is a good way to learn.

I have rendered my system unbootable many times in the beginning and it stills happens every now and again.

---

