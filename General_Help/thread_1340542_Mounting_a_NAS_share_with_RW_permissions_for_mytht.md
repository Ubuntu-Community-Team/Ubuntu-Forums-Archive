---
title: "Mounting a NAS share with RW permissions for mythtv"
date: 2009-11-28
forum: General Help
---

### Post by outleradam on 2009-11-28
I am trying to mount a network share.  it is my Network Attached Storage at SMB://192.168.1.1/public/Video.  Mythtv will record a job, compress it, then run a renaming app for SxxExx and copy it to my NAS.  I would like to mount it in the /home/mythtv dir for simplicity.   Here is what I have so far

```
sudo mount -t smbfs //192.168.1.1/public/Video /home/mythtv/storage -o credentials=/home/mythtv/.smbcredentials,file_mode=0777,dir_mode=0777
```The problem is that it is owned by root. the user account has R/W permission from the NAS, however I cannot seem to create a new folder with the permissions.  


```
adam@adam-desktop:/home/mythtv/storage$ ls -l
total 0
drwxrwxrwx 261 root root 0 2009-11-07 05:26 Movies
drwxrwxrwx  11 root root 0 2009-11-20 10:00 shows

```I have tried this
```
adam@adam-desktop:/home/mythtv/storage$ sudo -s
root@adam-desktop:/home/mythtv/storage# mkdir hi
mkdir: cannot create directory `hi': Permission denied
root@adam-desktop:/home/mythtv/storage#

```and I have tried this
```
sudo chown -R mythtv:mythtv /home/mythtv/storage/Video
``` which returns a whole bunch of operation not permitted errors.

I can easily log in using the ubuntu GUI connect to a shared disk, smb://user@192.168.1.1/   It gives me full permissions this way.

How can I make a share automatically mount to a folder at startup and have permissions?

---

### Post by dcstar on 2009-11-29
> **outleradam said:**
> I am trying to mount a network share.
........
How can I make a share automatically mount to a folder at startup and have permissions?

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

