---
title: "something is seriously wrong with my permissions"
date: 2009-11-20
forum: General Help
---

### Post by linuxgrrl on 2009-11-20
hello,
I have a small-ish hard drive with mythbuntu 9.10rc1 installed, and a second, much larger drive with all my photos and songs on it.  The partitions of the larger drive are mounted under /media/photos and /media/music, using the following lines in /etc/fstab:

```
/dev/sdb1       /media/music            ext3    defaults 1  2
/dev/sdb2       /media/home_video       ext3    defaults 1  2
/dev/sdb3       /media/photos           ext3    defaults 1  2
```

I've made the permissions pretty open I think:
```
mary@mythbox:/media$ ls -la
total 32
drwxrwxrwx  8 root root 4096 2009-11-09 19:58 .
drwxr-xr-x 22 root root 4096 2009-11-16 20:23 ..
lrwxrwxrwx  1 root root    6 2009-11-06 21:03 cdrom -> cdrom0
drwxr-xrw- 18 mary root 4096 2009-11-17 20:53 music
drwxr-xrwx  3 root root 4096 2009-11-20 22:30 mythvideo
drwxrwxrwx 12 mary root 4096 2009-11-19 13:41 photos
```

Yet none of my songs will play (neither rhythmbox nor banshee) and my photos are greyed out when I try to import into F-spot.  These collections were all created on a prior version of Ubuntu, then copied from an external drive to the local drive. 

Sure seems like something is wrong with my perms or how I am mounting these ... but what?

---

### Post by eicos on 2009-11-20
If you're not in a multi-user environment, why not just set all of your music/pictures/video permissions to 777? ```
chmod -R 777 /media
``` I'd imagine that would eliminate your problem.

---

### Post by linuxgrrl on 2009-11-21
Ok, thanks, I tried that and it changed the permissions but songs still won't play and photos are still greyed out.
help!

---

### Post by linuxgrrl on 2009-11-21
bump!  
there must be something very simple that I'm doing wrong!

---

