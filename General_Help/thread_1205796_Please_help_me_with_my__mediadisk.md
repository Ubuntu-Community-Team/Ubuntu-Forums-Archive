---
title: "Please help me with my  /media/disk"
date: 2009-07-06
forum: General Help
---

### Post by paparozoumis on 2009-07-06
I guess it will be easy for you to sort it out... 

I deleted some folders off that /media/disk (including the *user* folder among others) and that space on the  hard disk became unavailable. I cannot write anything on it at all. 
It's completely empty now so there will be no problem if I have to do any kind of formating or anything. 

What is it I can do to bring it back in life?
Computer works fine besides that, so deleting those fodlers from /media/disk hasn't influenced its working condition... 

Any help?

---

### Post by oldos2er on 2009-07-06
Can you post the output from this command:
```
sudo fdisk -l
```

---

### Post by Ascenti0n on 2009-07-06
can the files/folders not be restored from the wastebasket?

---

### Post by paparozoumis on 2009-07-06
> **oldos2er said:**
> Can you post the output from this command:
```
sudo fdisk -l
```

with pleasure

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       30075   212282910    5  Extended
/dev/sda5            3648        3769      979933+  82  Linux swap / Solaris
/dev/sda6            3770       30075   211302913+   b  W95 FAT32

```

---

### Post by paparozoumis on 2009-07-06
> **Ascenti0n said:**
> can the files/folders not be restored from the wastebasket?

When I realised that the disk was unusable, they were gone :(

---

### Post by oldos2er on 2009-07-06
So you just have the one hard disk? Can you post the output of **mount** ?

 I hope by "user folder" you don't mean /usr

---

### Post by paparozoumis on 2009-07-07
> **oldos2er said:**
> So you just have the one hard disk? Can you post the output of **mount** ?

 I hope by "user folder" you don't mean /usr

Sorry for the delay but time difference and work kept me away off my computer...

This is the mount output 

```
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,commit=600)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gigas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gigas)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal,commit=600)
```

To be more precise, the /media/disk is actually just a  partition of the one and only hard disk of my laptop. "/Media/disk" is just the way Ubuntu sees this partition. te time we are speaking now, the media/disk has no contents at all. 

What I deleted back then was not  /usr. It was the /gigas, /lost+found and two more folders of which I can't recall the names and all of them were absolutely empty.  

Thanks for taking the time to help, anyway.....

---

### Post by michy99 on 2009-07-07
If I understand correctly, you have deleted everything from /dev/sda6 which is mounted at /media/disk. For some reason you are unable to use this partition. What is the output of these commands?```
dh -f
ls -la /media/disk
```

---

### Post by paparozoumis on 2009-07-07
> **michy99 said:**
> If I understand correctly, you have deleted everything from /dev/sda6 which is mounted at /media/disk. For some reason you are unable to use this partition. What is the output of these commands?```
dh -f
ls -la /media/disk
```

```

dh -f
Unknown option: f
dh: warning: unknown options will be a fatal error in a future debhelper release
dh: cannot read debian/control: No such file or directory
```

```

ls -la /media/disk
total 12
drwxr-xr-x 2 root root 4096 2009-06-24 21:22 .
drwxr-xr-x 4 root root 4096 2009-07-06 19:56 ..
-rw-r--r-- 1 root root  184 2009-01-15 23:47 .asoundrc

```

---

### Post by michy99 on 2009-07-07
Sorry, the dyslexia strikes again. The first command should have been:```
df -h
```Also what do you get for ```
ls -ld /media/disk
```

---

### Post by oldos2er on 2009-07-07
Have you tried formatting the partition with gparted, or some other program?

---

### Post by paparozoumis on 2009-07-07
> **michy99 said:**
> Sorry, the dyslexia strikes again. The first command should have been:```
df -h
```


OK... here's the new one :)
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G  5.3G   21G  21% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  568K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M  1.6M 1005M   1% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6             199G  188M  189G   1% /media/disk

```

What does this say? ? ?

---

### Post by paparozoumis on 2009-07-07
> **oldos2er said:**
> Have you tried formatting the partition with gparted, or some other program?

Not yet... 
Actually, I haven't searched to this direction. 
If there's no other way I will try that too. There will be nothing to lose from that.....

---

### Post by michy99 on 2009-07-07
What happens if you try to save a file to the disk?```
touch/media/disk/test
```

---

### Post by paparozoumis on 2009-07-07
> **paparozoumis said:**
> Not yet... 
Actually, I haven't searched to this direction. 
If there's no other way I will try that too. There will be nothing to lose from that.....

Just downloaded and installed gparted. 
I saw that I can format that partition to different file systems. If I decide to go this way, which one should I choose? (It's ext3, now)....

---

### Post by paparozoumis on 2009-07-07
> **michy99 said:**
> What happens if you try to save a file to the disk?```
touch/media/disk/test
```


This is what I get:
Error opening file '/media/disk/catalogue Duro Stick.pdf': Permission denied

Never mind about the name of the file.. It's the first I got to try it....

---

### Post by paparozoumis on 2009-07-07
I have something here... 
I tried to copy manually the file and I got the permission denied. 
I sudo copied it and it went through with no hesitation. 

So, OBVIOUSLY it's a permission thing and the question that arises now is: How do I restore the permission back to normal, without having to use sudo every time?

---

### Post by michy99 on 2009-07-07
If there is nothing on that partition you care about, then reformatting is probably the best way to go. I would stick with ext3, unless you need to access it from a Windows system. In that case I would use NTFS.

---

### Post by paparozoumis on 2009-07-07
OK.. I formatted the partition to ext3 again. 
After that, one folder was automatically added: lost+found.
Besides that, NOTHING has changed as I still get that permission warning and I can't do anything inside that partition. 
the only way to use it is by sudoing every command through a terminal.... Not really handy....

---

### Post by paparozoumis on 2009-07-07
Problem solved, everyone :guitar::guitar:):P

Here's what I did. 
It was clear that it was a permission thing. 
I tried to change permissions through Properties of /disk/media but I got the message "The permissions of the "disk" could not be determined". It wouldn't allow me to do anything. 

I run 'gksudo nautilus' and this gave me the authorization to change things. I edited the Permissions to everyone to be able to write and delete files and.... voila... My problem solved. I can use again the partition :guitar::guitar::guitar:

Thank you guys. You helped me find the solution a lot with your ideas.... 
hail :)

---

### Post by oldos2er on 2009-07-07
For your user to take ownership of that partition, you would run
```
sudo chown -R username:username /media/disk
```
where "username" is your user.

---

### Post by paparozoumis on 2009-07-07
> **oldos2er said:**
> For your user to take ownership of that partition, you would run
```
sudo chown -R username:username /media/disk
```
where "username" is your user.

Hey oldos.. 
Thanks for your help. 
It works now the way I want it.
If I find in the future that it's not OK, I will have your advise in mind. 
Thanks again....

---

