---
title: "fstab and NTFS mount permissions, non-executable files, executable folders"
date: 2010-07-21
forum: General Help
---

### Post by Superkuh on 2010-07-21
I'm using Ubuntu 9.04 and I have an NTFS hard drive I am trying to mount without executable permissions for files, but with them for folders*. I've tried a lot of things in /etc/fstab, including but not entirely consisting of the below commented out lines.

#/dev/sdc1 /media/tre     ntfs-3g    defaults 0 0
#/dev/sdc1 /media/tre     ntfs-3g    auto,users,rw,noexec 0 0
#/dev/sdc1 /media/tre	ntfs-3g	defaults,locale=en_US.utf8,users,rw,noexec,umask=0000,fmask=0111 0 0
#/dev/sdc1 /media/tre	ntfs-3g		defaults,dmask=002,fmask=113,gid=plugdev 0 0
#/dev/sdc1 /media/tre	ntfs-3g		rw,umask=0000,fmask=0111,gid=plugdev 0 0 
#/dev/sdc1 /media/tre	ntfs-3g		ro,umask=0000,fmask=0111 0 2
#/dev/sdc1 /media/tre 	ntfs-3g		rw,dmask=002,fmask=113,gid=plugdev,uid=tre 0 2
#/dev/sdc1 /media/tre 	ntfs-3g		defaults,locale=en_US.utf8,users,nonexec,dmask=002,fmask=113,gid=plugdev,uid=tre 0 0
/dev/sdc1 /media/tre	ntfs-3g		auto,users,dmask=027,fmask=137,gid=tre,uid=tre,locale=en_US.utf8 0 0

No matter what I did in /etc/fstab, which was definitely being changed and saved with proper permissions, the output of the below mount -l did not change and the files in /home/tre would be executable. It is like fstab is not being used?

$ sudo mount -a
$ mount -l
/dev/sdc1 on /media/tre type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096) []

This set of permissions always came (after mount -a) with root:root ownership no matter the uid or gid specified as well. I have vague ideas about uDev interference but no idea on how to check them.

What options should I use in fstab, or what alternative systems should I be editing, to make files from the NTFS drive non-executable but folders executable? 

*I require this so that I can share the files over http with thttpd that has been configured to disallow executable files.

---

### Post by Timmyson on 2010-08-18
```
/dev/sda4       /media/windows  ntfs    rw,nosuid,nodev,noatime,allow_other,umask=0000,fmask=0111 0 0
```

Is my fstab line and it works (I got it from [here]("http://www.linuxquestions.org/questions/slackware-14/mount-ntfs-so-that-files-are-not-executable-buts-directories-are-363315/")).

It's possible it has something to do with the fuse (or fuseblk) driver instead of ntfs-3g?  You might want to try switching (package fuse-utils).

---

### Post by Timmyson on 2010-08-18
I can verify this works on my 10.04 and 9.10.

Thanks for making me try some research on this again, I hadn't tried to find an answer for years.

---

