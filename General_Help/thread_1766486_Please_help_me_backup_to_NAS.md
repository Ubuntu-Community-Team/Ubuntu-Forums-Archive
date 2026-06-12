---
title: "Please help me backup to NAS"
date: 2011-05-24
forum: General Help
---

### Post by tidmarsh on 2011-05-24
Please help me backup my laptop (running Maverick Meerkat) to a Netgear ReadyNAS NV+.  I can use Nautilus to browse to the NAS, and I can read and write to the network drives with Nautilus. What I would like to do is use Back in Time and rsync to backup my laptop to the NAS, but I cannot figure out a way to mount the NAS. I've tried following[ the tutorial for mounting a cifs drive]("http://ubuntuforums.org/showthread.php?t=288534")  and I've also tried mounting it as an nfs drive according to [this tutorial]("http://ubuntuforums.org/showthread.php?t=249889"). In both cases, when I try to use the mount command, I get the following error:
```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```My NAS has an IP address of //192.168.1.72 and netbios //nas-96-df-86/; I've tried mounting it using both names to no avail. I have enabled nfs, cifs, and rsync in the NAS control panel, and I've set the workgroup name on my laptop to match the NAS. On my laptop, I have created a mount point at /media/backup, andI have used chmod to change the permissions on the mount point to 777. I've tried adding the following options to the mount command, both individually and in combination: 
```
-o guest,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777
```Every single time, I get error(13): Permission denied.

The closest I've come to being able to backup to the NAS is using the .gvfs mount point in Back in Time. When I browse to the mount point and start the snapshot, Back in Time creates the directory structure, but does not copy any files. I seem to be having the same problem mentioned in [this Launchpad question]("https://answers.launchpad.net/backintime/+question/137178") (which links to [this suggestion]("http://backintime.le-web.org/2009/05/10/files-not-copied-when-backup-directory-is-on-smbfs/")). There is on "-o" option for nvfs, though, so the suggestion doesn't seem to help.

I'm becoming increasingly frustrated that it is so easy to browse to the network drive in Nautilus, but so maddeningly difficult to save a backup to the same drive. 

Finally, what I want to do is back up my laptop to a network drive on an NAS and synchronize a directory full of photos between the laptop and the NAS. I've been beating my head against a wall trying to mount the NAS to use rsync and Back in Time. Is there some (easier!?) way to accomplish these goals? Should I be doing something completely different?

Thanks for your help.

---

