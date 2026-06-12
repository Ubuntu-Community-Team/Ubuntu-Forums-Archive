---
title: "mhddfs line in fstab... syntax error?"
date: 2009-10-19
forum: General Help
---

### Post by gobbledigook on 2009-10-19
hi!

trying out [mhddfs]("http://manpages.ubuntu.com/manpages/karmic/man1/mhddfs.1.html") and can get it to work from cli fine.... but for some reason it just won't work from fstab :(

any ideas? am i just going blind!?!? 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=022570b1-427d-48ab-bed4-719133203358 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=3a2781bd-eace-4a90-a2a3-11b8b06eb4c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda1
#/dev/sda1      /media/movies-and-other-stuff   auto    defaults        0       0
# /dev/sdb1
#/dev/sdb1      /media/swap     auto    defaults        0       0
# /dev/sdc1
#/dev/sdc1      /media/series   auto    defaults        0       0
#mhddfs
mhddfs#/media/movies-and-other-stuff/movies-music-and-stuff,/media/swap/swap/,/media/series/series /media/server/ fuse logfile=/var/log/mhddfs.log 0 0

```

```
server@server:~$ sudo mount mhddfs
mount: can't find mhddfs in /etc/fstab or /etc/mtab

```

---

### Post by Giblet5 on 2009-10-19
What happens when you do that via ```
sudo mount -a
```

Did you really intend to mount these directories to "/media/server/" instead of "/media/server"?

That looks like a typo to me...

---

### Post by Giblet5 on 2009-10-19
Also, it looks like the source directories are not automounted.

It might be more helpful to create a few dummy directories and test it first...since this stuff is beta and all...

```
sudo mkdir /home/dummy1 /home/dummy2 /home/dummies
sudo echo Test1 > /home/dummy1/Test1.txt
sudo echo Test2 > /home/dummy2/Test2.txt
sudo mhddfs /home/dummy1,/home/dummy2 /home/dummies
```

Verify the results.

Create an /etc/fstab entry.

Do a mount -a and verify.

THEN start working with actual filesystems that have stuff you didn't really want scrambled...

---

### Post by gobbledigook on 2009-10-19
hey:) thanx for your reply!

i took another look at it... and as always when you've been bashing away at something for a while, your right! my syntax is a little squiffy!

after a bit of fiddling i now have the entry in my fstab:
```

mhddfs#/media/movies-and-other-stuff/,/media/swap/,/media/series /media/server

```

however what i was forgetting is that mhddfs will only merge folders... i had #-out my mountpoints and was trying to get it to mount them as if they were there! ie /media/series doesn't exist because i need to mount it first as /dev/sda1 > /media/series... i've been trying to get it to mount the disk, but when it errored i just switched to the 'folder' names!!

d'oh! so as these are shared... i need to unshare /media/series /media/swap etc... in smb conf and just share /media/server.. and obvously amend the conf's of progs which write to these folders to /media/server/swap etc...

thanx for your help!!

---

