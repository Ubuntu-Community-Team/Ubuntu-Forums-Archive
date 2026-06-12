---
title: "Permanently mounted network drive folder doesn't show all files"
date: 2012-05-16
forum: General Help
---

### Post by AOBeta on 2012-05-16
I have a media server that I mounted permanently with this.. 

//192.168.1.10/Media/ /home/cameron/CMN cifs username=username,password=password,uid=cameron 0 0

I have also tried replacing "cifs" with "smbfs" with no difference.

..in fstab.  Anyway, when I try to access a specific folder it will only show a limited number of files, but if I mount the media server by opening "browse network" and going to the media server and accessing the folder that way, it will show all of the files.  Anyone have any ideas on how to fix this?

I'm on Ubuntu 12.04 and a linux noob.  Thanks.

---

### Post by dcstar on 2012-05-17
> **AOBeta said:**
> I have a media server that I mounted permanently with this.. 

//192.168.1.10/Media/ /home/cameron/CMN cifs username=username,password=password,uid=cameron 0 0

I have also tried replacing "cifs" with "smbfs" with no difference.

..in fstab.  Anyway, when I try to access a specific folder it will only show a limited number of files, but if I mount the media server by opening "browse network" and going to the media server and accessing the folder that way, it will show all of the files.  Anyone have any ideas on how to fix this?

I'm on Ubuntu 12.04 and a linux noob.  Thanks.

Mount it via Nautilus and then run this command to see all the options that should be used to mount it correctly:

```
mount
```

Copy those options to the fstab entry.

---

### Post by AOBeta on 2012-05-17
> **dcstar said:**
> Mount it via Nautilus and then run this command to see all the options that should be used to mount it correctly:

```
mount
```

Copy those options to the fstab entry.

Forgive me, I don't really understand what you mean.  I ran the mount command and this is what I got..

```
cameron@living-ubuntu:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cameron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cameron)

```

and don't know how to add it into my fstab entry though.

---

### Post by Morbius1 on 2012-05-17
Since I don't have an answer for why only a subset of folders is visible may I ask you what is wrong with "browse network" method?

---

### Post by AOBeta on 2012-05-17
> **Morbius1 said:**
> Since I don't have an answer for why only a subset of folders is visible may I ask you what is wrong with "browse network" method?

It is just a more convient to have it mount automatically and it helps with browsing through xbmc for me.

---

### Post by dcstar on 2012-05-18
> **AOBeta said:**
> Forgive me, I don't really understand what you mean.  I ran the mount command and this is what I got..

```
cameron@living-ubuntu:~$ mount
........
gvfs-fuse-daemon on /home/cameron/.gvfs type fuse.gvfs-fuse-daemon (**rw,nosuid,nodev,user=cameron**)

```

and don't know how to add it into my fstab entry though.

```
gksudo gedit /etc/fstab
```

---

### Post by Morbius1 on 2012-05-18
> **AOBeta said:**
> It is just a more convient to have it mount automatically and it helps with browsing through xbmc for me.
Then use gigolo to automount: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Then create a bookmark to the .gvfs folder in your home directory:
```
nautilus $HOME/.gvfs
```When nautilus opens up immediately create a bookmak: Bookmarks > Create Bookmark.

It will create a ".gvfs" bookmark and show up in Nautilus and on all the "Open" and "Save As" dialog boxes on the left side panel.

---

### Post by AOBeta on 2012-05-18
> **dcstar said:**
> ```
gksudo gedit /etc/fstab
```

Right, I already know how to open fstab and edit it, but what I'm a supposed to add to it?  I'm I just supposed to copy/paste everything that appears with the mount command into the fstab?  I'm confused.

---

### Post by AOBeta on 2012-05-27
bump

---

