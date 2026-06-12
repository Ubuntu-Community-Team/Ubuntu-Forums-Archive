---
title: "cdrom mounts on /media/....."
date: 2010-04-17
forum: General Help
---

### Post by snappy46 on 2010-04-17
In am running Ubuhtu 9.10; my problem is that everytime I insert a cd or DVD in my DVD/burner it mounts the DVD under the /media folder under a directory normally named the disk volume. Although there are nothing wrong with that and I can access my cd or dvd from there it makes it very hard to share the cdrom using samba since the name of the directory changes every time a new DVD/CD is inserted.  I am trying to share the cdrom with my media player using samba but without success.  Even if I use the share folder option in nautilus to share the folder I can see it on my media player but when I try to access it; it ask for user and password.  Once I enter the user name and password of the user where the cdrom is mounted it's still telling that logon fail and I am unable to access the cdrom.

I guess what I need is a way so that when I insert a dvd/cd it gets mounted on /media/cdrom vs /media/whatever the volume is.  I need the location to remain the same so that the share works all the time no matter which cd/dvd I put in.  When I issue the mount -l command I can see that my dvd/cd is mounted on /dev/sr0.

I do have an entry in my fstab for a /media/cdrom0 and /media/cdrom1

Any help would be appreciated.  Thanks

---

