---
title: "mount"
date: 2012-03-06
forum: General Help
---

### Post by nrmurali on 2012-03-06
how to mount a directory of one linux  machine to another  linux machine 

using mount command

---

### Post by cryptotheslow on 2012-03-06
You could use sshfs or nfs amongst other ways.

I use sshfs to mount a directory from an ubuntu server on my laptop for example.

The server needs to have the openssh server process running on it.

Then to make my life easier and not have to remember the mount command in its entirety I made an addition to my /etc/fstab file like this:
```
# ubuserver share mount
crypto@ubuserver:/home/crypto/shared /home/crypto/ubuserver_shared fuse.sshfs noauto,user,allow_other 0 0
```Where:
crypto - is my username on both machines
ubuserver - is the name of my server, you could just as well use an IP address
/home/crypto/shared - is the location of the directory on the remote server
/home/crypto/ubuserver_shared - is the location on the laptop where I want the mounted dir to appear (create this dir first)
The "noauto" parameter means that the directory is not mounted at boot up time.

What this results in is an "ubuntuserver_shared" icon appearing in Nautilus that I can just click on - which pops up an OpenSSH dialog box for the password and then mounts the directory once entered.

Alternatively from a command line:
```
mount ubuntuserver_shared
```You need to get SSH working first. Apparently NFS is simple to use as well, but as I've not tried it I can't comment.

---

